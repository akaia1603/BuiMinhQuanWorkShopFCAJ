---
title: "Chờ & copy Endpoint"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.8.2.</b> "
---

## Các bước

1. Tạo database và đợi tới khi status chuyển **Available**.
2. Vào tab **Connectivity & security**, copy lại **Endpoint**.

![RDS instance Available với Endpoint](/images/5-Workshop/5.8-TaskManager-RDS/03-rds-available.png)

*Trang RDS instance ở trạng thái Available, hiển thị đầy đủ Endpoint.*

> **Ghi chú:** RDS đang chạy MySQL **8.4** (kết quả khi kết nối thử trả về `Server version: 8.4.9`). Nếu đã bỏ trống mục "Initial database name", cần tự tạo database trước khi khởi động backend — xem Troubleshooting tại [5.8.3](5.8.3-Verify-and-Troubleshooting).