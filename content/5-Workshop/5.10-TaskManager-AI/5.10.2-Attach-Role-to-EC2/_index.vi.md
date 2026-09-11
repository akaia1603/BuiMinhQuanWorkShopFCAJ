---
title: "Gắn role vào EC2"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.10.2.</b> "
---

## Bước 2 — Gắn role vào EC2

1. **EC2 Console → chọn instance đang chạy backend → Actions → Security → Modify IAM role**.
2. Chọn role vừa tạo → **Update IAM role**.

![Thay đổi IAM role trên EC2](/images/5-Workshop/5.10-TaskManager-AI/04-ec2-modify-iam-role.png)

*Chọn `taskmanager-ec2-comprehend-role` trong "Modify IAM role".*

![EC2 instance hiển thị IAM role](/images/5-Workshop/5.10-TaskManager-AI/05-ec2-iam-role.png)

*Mục "IAM role" trong EC2 instance details hiển thị role vừa gán.*

> **Xác nhận role từ EC2 (IMDSv2):** instance bật **IMDSv2 (Required)** nên lệnh metadata thông thường sẽ trả về trống. Cần lấy token trước:
>
> ```bash
> TOKEN=$(curl -s -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
> curl -s -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/meta-data/iam/security-credentials/
> ```
>
> Trả về tên role (`taskmanager-ec2-comprehend-role`) là đã gắn thành công.