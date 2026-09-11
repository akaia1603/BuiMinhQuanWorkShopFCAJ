---
title: "Khởi tạo RDS instance"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.8.1.</b> "
---

## Các bước

1. **RDS → Create database** → Engine: **MySQL**, Template: **Free tier**.

![Tạo RDS database](/images/5-Workshop/5.8-TaskManager-RDS/01-rds-create.png)

*Trang "Create database" — MySQL, Free tier.*

2. DB instance identifier: `taskmanager-db`. Master username: `admin`, đặt password mạnh và **lưu lại cẩn thận — không thể xem lại**.
3. DB instance class: `db.t3.micro`. **Public access: No** (giữ RDS ở chế độ private).
4. VPC security group: **Create new**, đặt tên `rds-sg`. Initial database name: `taskmanager`.

![Cấu hình RDS instance](/images/5-Workshop/5.8-TaskManager-RDS/02-rds-config.png)

*Cấu hình DB — private, không public access.*

5. **Create database**, đợi tới khi status chuyển **Available**.