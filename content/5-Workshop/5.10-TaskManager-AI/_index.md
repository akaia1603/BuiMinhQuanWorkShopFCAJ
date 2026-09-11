---
title: "Task Manager — Amazon Comprehend AI"
date: 2026-09-01
weight: 10
chapter: false
pre: " <b> 5.10. </b> "
---

## Goal

Fulfil CLO3: integrate AI (Amazon Comprehend) into the backend. Instead of hardcoding an Access Key / Secret Key, permissions are granted through an **IAM Role attached to the EC2 instance** — the AWS best practice.

## Subsections

1. [Create the IAM role](5.10.1-Create-IAM-Role/) — EC2 trust, `ComprehendReadOnly`, `taskmanager-ec2-comprehend-role`.
2. [Attach the role to EC2](5.10.2-Attach-Role-to-EC2/) — Modify IAM role + IMDSv2 verification.
3. [Restart & verify](5.10.3-Restart-and-Verify/) — check `priority` and `aiKeyPhrases` in the response.
4. [Troubleshooting & code example](5.10.4-Troubleshooting-and-Code/) — activation issue and the `AiAnalysisService` excerpt.