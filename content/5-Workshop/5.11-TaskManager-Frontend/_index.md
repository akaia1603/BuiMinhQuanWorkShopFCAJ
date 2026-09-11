---
title: "Task Manager — frontend & E2E testing"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Goal

Expose the Task Manager UI on the web (over HTTP on port 80, ready to upgrade to HTTPS with Let's Encrypt) and verify the whole system end to end, including the AI-suggested priority.

## Subsections

1. [Point the frontend to the API](5.11.1-Point-Frontend-to-API/) — set `API_BASE` in `frontend/js/config.js`.
2. [Deploy with Nginx](5.11.2-Deploy-with-Nginx/) — install, server block, port 80 in the Security Group.
3. [End-to-end test](5.11.3-End-to-End-Test/) — register, projects, tasks, AI priority.
4. [Features & expected outcome](5.11.4-Features-and-Outcome/) — feature list and success criteria.
5. [Troubleshooting](5.11.5-Troubleshooting/) — permissions, CSS and JWT issues.