---
title: "Khởi chạy EC2"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.9.1.</b> "
---

## Bước 1 — Khởi chạy EC2

1. Khởi chạy EC2 instance (**Amazon Linux 2023, t3.micro**) trong cùng VPC với RDS, ở public subnet.

![Khởi chạy EC2 instance](/images/5-Workshop/5.9-TaskManager-EC2/01-ec2-launch.png)

*Đang khởi chạy instance Amazon Linux 2023 t3.micro.*

2. Security Group: mở **port 22 (nguồn: My IP)** và **port 8080 (nguồn: Anywhere)** (mở thêm **port 80** khi deploy frontend ở mục [5.11](../5.11-TaskManager-Frontend)).

![EC2 instance đang chạy](/images/5-Workshop/5.9-TaskManager-EC2/02-ec2-running.png)

*EC2 instance backend ở trạng thái Running.*