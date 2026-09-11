---
title: "Features & expected outcome"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.11.4.</b> "
---

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