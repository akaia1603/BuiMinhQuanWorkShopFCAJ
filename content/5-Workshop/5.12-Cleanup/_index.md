---
title: "Resource cleanup"
date: 2026-09-01
weight: 12
chapter: false
pre: " <b> 5.12. </b> "
---

## Goal

Remove every resource created during the internship so no unexpected charges appear after finishing — ideally keeping the month within the Free Tier.

## Steps

- **RDS:** **Stop** or **Delete** `taskmanager-db` (note: Stop only pauses for a maximum of 7 days, then AWS restarts it automatically).
- **EC2:** **Terminate** the instances used for the VPC workshop and the Task Manager API.
- **CloudFront + S3:** **Disable** then **Delete** the distribution; empty and **Delete** the S3 bucket.
- **Lambda + API Gateway + DynamoDB:** delete the Lambda function, the API Gateway, and the `fcaj-notes` DynamoDB table.
- **IAM Role:** may be kept (no charge) or deleted if unused.
- Finally check the **Billing Dashboard** to confirm no resource is generating charges.

## Expected outcome

- Billing dashboard shows only expected/Free Tier charges after cleanup

> **[Screenshot — insert later]:** the Billing Dashboard after cleanup showing costs within the expected range (optional — include only if the faculty requires it).