---
title: "Database design"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.7.3.</b> "
---

## Database design

Three main tables: `users`, `projects`, `tasks`. `tasks` adds two columns for the AI feature: `priority` (`LOW`/`MEDIUM`/`HIGH`, suggested by the AI) and `ai_key_phrases` (key phrases extracted by Comprehend).

Relationships: one user owns many projects (**1–N**); one project contains many tasks (**1–N**); a task can be assigned to one user (`assignee`, **N–1**).

![ERD — users / projects / tasks](/images/5-Workshop/5.7-TaskManager-Overview/02-erd.png)

*ERD of the three tables (drawn with draw.io): users / projects / tasks.*