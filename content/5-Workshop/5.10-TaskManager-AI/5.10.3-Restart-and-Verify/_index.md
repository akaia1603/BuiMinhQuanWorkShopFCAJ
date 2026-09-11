---
title: "Restart & verify"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.10.3.</b> "
---

## Step 3 — Restart & verify

1. Restart the backend service so the AWS SDK picks up the new permissions: `sudo systemctl restart taskmanager`.
2. Create a task with an urgent description (e.g. "Need to urgently fix a critical bug before the deadline").

![Task creation response with AI priority](/images/5-Workshop/5.10-TaskManager-AI/06-ai-priority-response.png)

*Task creation response with `priority = HIGH` and `aiKeyPhrases` filled automatically.*

## Expected outcome

- The task creation response includes `priority = HIGH` and `aiKeyPhrases` filled with the phrases Comprehend extracted
- No access keys in the code — permission comes from the instance role