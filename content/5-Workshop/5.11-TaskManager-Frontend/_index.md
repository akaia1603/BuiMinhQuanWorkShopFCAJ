---
title: "Task Manager — frontend & E2E testing"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Goal

Expose the Task Manager UI over HTTPS and verify the whole system end to end, including the AI-suggested priority.

## Step 1 — Point the frontend to the API

1. Edit `API_BASE` in `frontend/index.html` to the real EC2 address: `http://<EC2-Public-IP>:8080`.

## Step 2 — Deploy to S3 + CloudFront

1. Upload `index.html` to the S3 bucket, enable static website hosting, create the CloudFront distribution (repeat the flow from [5.4](5.4-S3-CloudFront/)).

## Step 3 — End-to-end test

1. Open the site via the CloudFront link.
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
- Each task shows a Priority badge and an "AI identified: ..." line

> **[Screenshot — insert later]:** (1) login/register screen; (2) project list; (3) task list showing the Priority badge and the "AI identified:" line under each task.