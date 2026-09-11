---
title: "Thành phần & công nghệ"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.7.2.</b> "
---

## Các thành phần chính

- **Frontend:** HTML/CSS/JavaScript thuần, phục vụ bởi **Nginx** chạy trên chính EC2 (cùng instance với backend); phương án S3 + CloudFront đã được thực hành riêng ở mục [5.4](../5.4-S3-CloudFront).
- **Backend:** REST API Java Spring Boot trên **EC2** (public subnet của VPC).
- **Database:** MySQL trên **Amazon RDS** (private subnet), chỉ nhận kết nối từ Security Group của EC2.
- **AI service:** **Amazon Comprehend** được EC2 gọi qua IAM Role (không hardcode Access Key) để phân tích sentiment và trích xuất từ khóa từ mô tả task.

## Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| Ngôn ngữ lập trình | Java 17 |
| Framework Backend | Spring Boot 3.3, Spring Security, Spring Data JPA |
| Xác thực | JWT (JSON Web Token), mã hóa mật khẩu BCrypt |
| Cơ sở dữ liệu | MySQL 8.x (Amazon RDS) |
| Dịch vụ AI | Amazon Comprehend (DetectSentiment, DetectKeyPhrases) |
| Frontend | HTML5, CSS3, JavaScript thuần (Fetch API), Nginx (web server) |
| Đóng gói & triển khai | Docker, Docker Compose |
| Hạ tầng Cloud | Amazon EC2, Amazon RDS, Amazon VPC, IAM Role |
| Công cụ build | Apache Maven |
| Công cụ kiểm thử API | Postman, curl |