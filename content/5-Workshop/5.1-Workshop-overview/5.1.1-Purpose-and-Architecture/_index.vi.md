---
title: "Mục đích & kiến trúc"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.1.1.</b> "
---

## Mục đích

Workshop này ghi lại toàn bộ thực hành AWS đã triển khai trong đợt thực tập FCAJ theo trình tự: chuẩn bị môi trường, giám sát chi phí, các workshop nền tảng về serverless và mạng, rồi tới dự án chính — **Task Manager API**, backend Java Spring Boot hoàn chỉnh trên **EC2 + RDS**, tích hợp AI **Amazon Comprehend** để tự động gợi ý mức độ ưu tiên cho task (đáp ứng CLO3).

Mỗi mục đều ghi rõ các bước thao tác trên AWS Console và kèm ảnh chụp màn hình tại mọi điểm cần minh chứng cho báo cáo.

## Kiến trúc (dự án chính)

| Thành phần | Công nghệ / dịch vụ |
|------------|---------------------|
| Frontend | HTML/CSS/JS tĩnh trên S3 + CloudFront |
| Backend | Java 17, Spring Boot 3.3 (Spring Security, Spring Data JPA) trên EC2 |
| Database | MySQL 8.0 trên Amazon RDS (private subnet) |
| AI | Amazon Comprehend — DetectSentiment, DetectKeyPhrases |
| Xác thực | JWT, mã hóa mật khẩu BCrypt |
| Đóng gói | Maven, Docker, Docker Compose |
| Hạ tầng | EC2, RDS, VPC, S3, CloudFront, IAM Role |

![Sơ đồ kiến trúc tổng thể](/images/5-Workshop/5.1-Workshop-overview/01-architecture.png)

*Sơ đồ: user → CloudFront/S3 → EC2 Spring Boot → RDS MySQL; EC2 → Amazon Comprehend qua IAM Role.*