---
title: "Tạo IAM Role"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.10.1.</b> "
---

## Bước 1 — Tạo IAM Role

1. **IAM → Roles → Create role**.

![Bắt đầu tạo IAM Role](/images/5-Workshop/5.10-TaskManager-AI/01-iam-create-role.png)

*Trang "Create role".*

2. Trusted entity: **AWS service** → Use case: **EC2**.
3. Ở bước Permissions, tìm và tick policy **`ComprehendReadOnly`**.

![Gắn policy ComprehendReadOnly](/images/5-Workshop/5.10-TaskManager-AI/02-iam-comprehend-policy.png)

*Chọn policy `ComprehendReadOnly`.*

4. Đặt tên role: `taskmanager-ec2-comprehend-role` → **Create role**.

![IAM Role đã tạo](/images/5-Workshop/5.10-TaskManager-AI/03-iam-role-created.png)

*IAM Role với policy ComprehendReadOnly đã gắn.*