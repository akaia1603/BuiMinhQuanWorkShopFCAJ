---
title: "Task Manager — frontend & E2E testing"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Goal

Expose the Task Manager UI on the web (over HTTP on port 80, ready to upgrade to HTTPS with Let's Encrypt) and verify the whole system end to end, including the AI-suggested priority.

## Step 1 — Point the frontend to the API

1. Edit `API_BASE` in `frontend/js/config.js` to the real EC2 address: `http://<EC2-Public-IP>:8080`.

## Step 2 — Deploy the frontend with Nginx on EC2

1. Install Nginx on EC2: `sudo yum install -y nginx`.
2. Copy the whole `frontend/` folder into `/usr/share/nginx/html/`, create a server block in `/etc/nginx/conf.d/taskmanager.conf` (listen **80**, `root /usr/share/nginx/html`, `try_files $uri $uri/ /index.html;`).
3. Start and enable it: `sudo systemctl start nginx && sudo systemctl enable nginx`.
4. Open **port 80** in the EC2 Security Group (Custom TCP, source `0.0.0.0/0`).

> **Design note:** serving the frontend with Nginx on the same EC2 as the backend keeps them close together and reduces cost for a small project; the **S3 + CloudFront** option is practiced separately in section [5.4](5.4-S3-CloudFront/).

## Step 3 — End-to-end test

1. Open the site via `http://<EC2-Public-IP>`.
2. Register a new account, create a project, create tasks with different wording to observe different AI-suggested priorities, change task status, delete tasks/projects.

## Features

- Register a new account, sign in, receive a JWT token
- CRUD Projects
- CRUD Tasks inside each project
- Update task status (TODO / IN_PROGRESS / DONE)
- Assign a task to a member (assignee)
- AI-suggested **Priority** + key-phrase extraction (Amazon Comprehend) on every task create/update

## Expected outcome

- All flows work through the browser against the live backend
- Each task shows a Priority badge and an "AI identified: ..." line under it
- `curl -I http://localhost/css/style.css` returns `200 OK` (Content-Type: `text/css`)

## Troubleshooting

| Issue | Fix |
|-------|-----|
| The page loads but CSS/JS do not (403) | The `css/` and `js/` folders have mode `dr-x------` (500) — nginx cannot read them. Run `sudo chmod 755 /usr/share/nginx/html/css/ /usr/share/nginx/html/js/`, then `sudo chmod 644 /usr/share/nginx/html/css/* /usr/share/nginx/html/js/*`, followed by `sudo systemctl restart nginx` |
| The UI loses all styling and layout breaks | `style.css` had a syntax error (the `.stat-label` selector was missing a closing `}`) which made the browser skip the following CSS. Fixed the block; verified by counting balanced `{`/`}` |
| API calls return `403` after changing the JWT secret | The old token in the browser is invalid. Open the Console (F12), run `localStorage.clear()`, refresh the page and sign in again |

> **[Screenshot — insert later]:** (1) login/register screen; (2) project list; (3) task list showing the Priority badge and the "AI identified:" line under each task.