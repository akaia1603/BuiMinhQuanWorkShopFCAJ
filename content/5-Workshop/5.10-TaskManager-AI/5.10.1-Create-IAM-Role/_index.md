---
title: "Create the IAM role"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.10.1.</b> "
---

## Step 1 — Create the IAM role

1. **IAM → Roles → Create role**.

![Starting to create the IAM role](/images/5-Workshop/5.10-TaskManager-AI/01-iam-create-role.png)

*The "Create role" wizard.*

2. Trusted entity: **AWS service** → Use case: **EC2**.
3. In Permissions, find and tick the **`ComprehendReadOnly`** policy.

![Attaching ComprehendReadOnly](/images/5-Workshop/5.10-TaskManager-AI/02-iam-comprehend-policy.png)

*Selecting the `ComprehendReadOnly` policy.*

4. Name: `taskmanager-ec2-comprehend-role` → **Create role**.

![IAM role created](/images/5-Workshop/5.10-TaskManager-AI/03-iam-role-created.png)

*The IAM role with the attached ComprehendReadOnly policy.*