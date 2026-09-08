---
title: "Week 6 Worklog"
date: 2026-08-29
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Integrate the AI service (Amazon Comprehend) into the Task Manager backend via an IAM Role.
* Deploy the frontend on S3 + CloudFront, run end-to-end testing, and document the resource cleanup.

**Period:** 29/08/2026 – 04/09/2026

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Create IAM role `taskmanager-ec2-comprehend-role` with `ComprehendReadOnly` <br> - Attach the role to the EC2 instance and restart the systemd service | 31/08/2026 | 31/08/2026 | AWS IAM docs |
| 3 | - Implement `AiAnalysisService` in the backend (DetectSentiment, DetectKeyPhrases) <br> - **Test:** create a task with urgent wording → expect `priority = HIGH` + `aiKeyPhrases` | 01/09/2026 | 01/09/2026 | Amazon Comprehend docs |
| 4 | - Point the frontend `API_BASE` to the EC2 endpoint and upload the site to S3 <br> - Create the CloudFront distribution for the frontend | 02/09/2026 | 02/09/2026 | |
| 5 | - **E2E test:** register → create project/task → AI priority → change status → delete <br> - Document the cleanup steps (RDS, EC2, CloudFront, S3, API Gateway, Lambda, DynamoDB, VPC, IAM) | 03/09/2026 | 03/09/2026 | |
| 6 | - Verify the full feature set (CRUD + assignee + AI) and finalize the workshop write-ups | 04/09/2026 | 04/09/2026 | |

### Week 6 Achievements:

* Integrated Amazon Comprehend without any hardcoded credentials — permissions come from the instance IAM Role.
* Verified the AI-suggested priority and key-phrase extraction on task creation/update.
* Deployed the plain-JS frontend to S3 + CloudFront and tested the whole system end-to-end through the browser.
* Completed the feature set: JWT auth, CRUD projects/tasks, status updates, assignee, and AI insights.
* Documented a screenshot-based resource cleanup guide for the final report.