---
title: "Task Manager — triển khai EC2 & backend"
date: 2026-09-01
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

## Mục tiêu

Triển khai backend Java Spring Boot trên EC2 trong cùng VPC với RDS, đồng thời chỉ cho instance này kết nối được database.

## Các mục con

1. [Khởi chạy EC2](5.9.1-Launch-EC2/) — Amazon Linux 2023, t3.micro, ở public subnet.
2. [Cho phép EC2 kết nối RDS](5.9.2-Allow-EC2-to-Reach-RDS/) — mở port 3306 inbound từ Security Group của EC2.
3. [Cài Java & deploy](5.9.3-Install-Java-and-Deploy/) — build, copy jar, cấu hình `app.env`, chạy dưới systemd service.
4. [Xác minh & troubleshooting](5.9.4-Verify-and-Troubleshooting/) — kết quả mong đợi và lỗi thường gặp.