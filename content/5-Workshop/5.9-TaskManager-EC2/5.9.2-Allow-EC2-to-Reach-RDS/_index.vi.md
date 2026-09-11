---
title: "Cho phép EC2 kết nối RDS"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.9.2.</b> "
---

## Bước 2 — Cho phép EC2 kết nối RDS

1. Vào Security Group của RDS `rds-sg` → **Edit inbound rules**.

![Sửa inbound rules của Security Group RDS](/images/5-Workshop/5.9-TaskManager-EC2/03-rds-sg-inbound.png)

*Thêm inbound rule MySQL cho `rds-sg`.*

2. Thêm rule **MYSQL/Aurora (port 3306)**, Source: **Security Group của EC2** (không mở Anywhere).