---
title: "Attach the role to EC2"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.10.2.</b> "
---

## Step 2 — Attach the role to EC2

1. **EC2 Console → select the backend instance → Actions → Security → Modify IAM role**.
2. Choose the new role → **Update IAM role**.

![Modifying the IAM role on EC2](/images/5-Workshop/5.10-TaskManager-AI/04-ec2-modify-iam-role.png)

*Selecting `taskmanager-ec2-comprehend-role` in "Modify IAM role".*

![EC2 details showing the IAM role](/images/5-Workshop/5.10-TaskManager-AI/05-ec2-iam-role.png)

*The EC2 instance details showing the assigned IAM role.*

> **Verify the role from EC2 (IMDSv2):** the instance enables **IMDSv2 (Required)**, so the plain metadata request returns empty. A token is needed first:
>
> ```bash
> TOKEN=$(curl -s -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
> curl -s -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/meta-data/iam/security-credentials/
> ```
>
> Returning the role name (`taskmanager-ec2-comprehend-role`) means it is attached successfully.