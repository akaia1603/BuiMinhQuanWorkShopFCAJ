---
title: "Tổng quan workshop"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

## Mục đích

Phần này ghi lại toàn bộ thực hành AWS đã triển khai trong đợt thực tập FCAJ theo trình tự: chuẩn bị môi trường, giám sát chi phí, các workshop nền tảng về serverless và mạng, rồi tới dự án chính — **Task Manager API**, backend Java Spring Boot hoàn chỉnh trên **EC2 + RDS**, tích hợp AI **Amazon Comprehend** để tự động gợi ý mức độ ưu tiên cho task (đáp ứng CLO3).

Mỗi mục đều ghi rõ các bước thao tác trên AWS Console và đánh dấu `[CHỤP MÀN HÌNH]` tại điểm cần chụp màn hình làm minh chứng cho báo cáo.

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

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** sơ đồ kiến trúc tổng thể (user → CloudFront/S3 → EC2 Spring Boot → RDS MySQL; EC2 → Amazon Comprehend qua IAM Role).

## Điều kiện tiên quyết

- Tài khoản AWS quyền admin (hoặc IAM User đủ quyền trên S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch, IAM)
- Trình duyệt web (Chrome / Firefox / Edge)
- Công cụ kiểm thử API: Postman hoặc curl
- JDK 17, Maven, Docker cài trên máy cá nhân (build/test trước khi deploy)

## Region

Toàn bộ dịch vụ triển khai tại **`ap-southeast-1`** (Singapore) — mọi thứ nằm chung một region để tránh lỗi kết nối chéo vùng. Riêng Billing Alarm phải tạo tại **`us-east-1`** (xem [5.3](5.3-Cost-Monitoring/)).

## Thứ tự thực hiện

Làm **5.2 → 5.11** theo thứ tự; các mục sau phụ thuộc vào tài nguyên VPC, EC2 và RDS của các mục trước. **5.12** ghi lại quy trình dọn dẹp.

## Kỹ năng và công cụ

- Thiết kế và triển khai REST API theo chuẩn RESTful
- Xác thực JWT + Spring Security
- Thiết kế cơ sở dữ liệu quan hệ + ORM (Spring Data JPA / Hibernate)
- Triển khai lên AWS (EC2, RDS) theo mô hình mạng an toàn (VPC, Security Group, private subnet cho database)
- Tích hợp AI qua IAM Role (không hardcode credentials)
- Đóng gói bằng Docker / Docker Compose
- Giám sát và kiểm soát chi phí (Budgets, CloudWatch)
- Kiểm thử API bằng Postman / curl

## Checklist xác minh

- [ ] Budget `FCAJ-Budget` và Billing Alarm hoạt động (cảnh báo tại 50% / 80%)
- [ ] Website tĩnh truy cập được qua link CloudFront với HTTPS
- [ ] Serverless API GET/POST `/notes` hoạt động với DynamoDB
- [ ] VPC 2-tier có public/private subnet và SSH được vào EC2
- [ ] RDS private; EC2 kết nối MySQL port 3306 qua Security Group
- [ ] Tạo task trả về `priority` + `aiKeyPhrases` từ Amazon Comprehend
- [ ] Dọn dẹp toàn bộ tài nguyên sau khi nộp báo cáo