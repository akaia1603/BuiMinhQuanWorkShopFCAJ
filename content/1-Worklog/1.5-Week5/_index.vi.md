---
title: "Worklog Tuần 5"
date: 2026-08-22
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Thiết kế VPC 2-tier và thiết lập nền tảng mạng cho dự án chính.
* Cấp phát RDS MySQL và triển khai backend Task Manager Spring Boot trên EC2.

**Thời gian:** 22/08/2026 – 28/08/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Thiết kế VPC 2-tier: VPC `10.0.0.0/16`, public subnet `10.0.1.0/24` và private subnet `10.0.2.0/24` tại 2 AZ <br> - Tạo Internet Gateway, route table public và Security Group (SSH My IP + HTTP) | 24/08/2026 | 24/08/2026 | Tài liệu AWS VPC |
| 3 | - Khởi chạy EC2 (Amazon Linux 2023, t2.micro) trong public subnet và kiểm thử SSH | 25/08/2026 | 25/08/2026 | |
| 4 | - Thiết kế database Task Manager (users/projects/tasks) và bộ công nghệ <br> - Tạo RDS MySQL `taskmanager-db` (Free tier, db.t3.micro, Public access: No) | 26/08/2026 | 26/08/2026 | Tài liệu AWS RDS |
| 5 | - Thêm inbound 3306 vào Security Group RDS với source là Security Group của EC2 <br> - Build project Spring Boot trên local (`mvn clean package -DskipTests`) | 27/08/2026 | 27/08/2026 | Tài liệu Spring Boot |
| 6 | - Copy file `.jar` lên EC2 bằng scp; tạo `app.env` và systemd service <br> - **Kiểm thử:** đăng ký qua `POST /api/auth/register` và xác nhận kết nối RDS | 28/08/2026 | 28/08/2026 | |

### Kết quả đạt được tuần 5:

* Xây dựng VPC 2-tier an toàn khớp với kiến trúc của dự án chính.
* Cấp phát RDS MySQL private chỉ kết nối được từ Security Group của EC2.
* Triển khai backend Task Manager Spring Boot trên EC2 dưới dạng systemd service, JWT register hoạt động với RDS.
* Áp dụng Security Group ít quyền nhất cho tầng database (không mở 3306 public).