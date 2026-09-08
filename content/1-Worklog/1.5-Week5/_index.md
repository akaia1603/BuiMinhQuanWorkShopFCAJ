---
title: "Week 5 Worklog"
date: 2026-08-22
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Hand off the client with the login flow to the team and implement CI/CD with GitHub Actions.
* Implement IAM permission boundaries and validate CodeDeploy deployment capability.

**Period:** 22/08/2026 – 28/08/2026

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Finalize client login UI and session handling; hand off codebase with documented auth + netcode interfaces | 24/08/2026 | 24/08/2026 | |
| 3 | - Set up the GitHub repository structure and create the initial GitHub Actions workflow for build and deploy <br> - Configure S3 static website hosting for the browser client and test the first automated deploy | 25/08/2026 | 25/08/2026 | GitHub Actions docs |
| 4 | - Study IAM Permission Boundaries and least-privilege deploy patterns <br> - Register GitHub OIDC identity provider in IAM (no long-lived access keys) | 26/08/2026 | 26/08/2026 | AWS IAM docs |
| 5 | - Create a deploy role with trust policy scoped to the GitHub repo and attach permissions <br> - Configure repository secrets (`AWS_ROLE_ARN`, `COGNITO_*`, `ASSETS_BUCKET`, etc.) | 27/08/2026 | 27/08/2026 | |
| 6 | - **Test:** Push to GitHub → verify S3 sync, Lambda update, and CodeDeploy job success | 28/08/2026 | 28/08/2026 | |

### Week 5 Achievements:

* Delivered a working client handoff package with a login flow and netcode stubs for the team.
* Created the project repository, established branching conventions, and implemented the first GitHub Actions workflow.
* Created the S3 assets bucket with static website hosting, a public-read policy, and CORS configuration.
* Eliminated static AWS access keys from CI by implementing GitHub OIDC → IAM role authentication.
* Applied IAM Permission Boundaries to constrain deploy-role capabilities.
* Configured `FightingGameServerInstanceRole` and MatchMaker Lambda permissions (DynamoDB, EC2 `DescribeInstances`).
* Verified the end-to-end deploy pipeline: GitHub push → Actions → S3 client sync + CodeDeploy.
