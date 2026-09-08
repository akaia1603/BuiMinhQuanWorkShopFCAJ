---
title: "Task Manager — thiết lập RDS MySQL"
date: 2026-09-01
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

## Mục tiêu

Cấp phát database MySQL trên RDS, giữ ở chế độ private để chỉ backend EC2 kết nối được.

## Các bước

1. **RDS → Create database** → Engine: **MySQL**, Template: **Free tier**.
2. DB instance identifier: `taskmanager-db`. Master username: `admin`, đặt password mạnh và **lưu lại cẩn thận — không thể xem lại**.
3. DB instance class: `db.t3.micro`. **Public access: No** (giữ RDS ở chế độ private).
4. VPC security group: **Create new**, đặt tên `rds-sg`. Initial database name: `taskmanager`.
5. **Create database**, đợi tới khi status chuyển **Available**.
6. Vào tab **Connectivity & security**, copy lại **Endpoint**.

## Kết quả mong đợi

- RDS instance `taskmanager-db` ở trạng thái `Available`
- Private — không mở public, chỉ cho kết nối từ Security Group của EC2

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** trang RDS instance ở trạng thái Available, hiển thị đầy đủ Endpoint.