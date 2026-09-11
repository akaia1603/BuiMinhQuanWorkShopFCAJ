---
title: "Task Manager — thiết lập RDS MySQL"
date: 2026-09-01
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

## Mục tiêu

Cấp phát database MySQL trên RDS, giữ ở chế độ private để chỉ backend EC2 kết nối được.

## Các mục con

1. [Khởi tạo RDS instance](5.8.1-Launch-RDS-Instance/) — MySQL free tier, `taskmanager-db`.
2. [Chờ & copy Endpoint](5.8.2-Wait-and-Copy-Endpoint/) — lấy địa chỉ database.
3. [Xác minh & troubleshooting](5.8.3-Verify-and-Troubleshooting/) — kết quả mong đợi và lỗi thường gặp.