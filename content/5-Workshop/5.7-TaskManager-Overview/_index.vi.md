---
title: "Task Manager API — tổng quan, công nghệ & database"
date: 2026-09-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

## Mô tả bài toán

Task Manager API là REST API backend phục vụ quản lý công việc/dự án ở quy mô nhỏ: người dùng đăng ký/đăng nhập, tạo và quản lý các **Project**, tạo/quản lý các **Task** thuộc từng project với trạng thái `TODO`, `IN_PROGRESS`, `DONE`. Mỗi task khi tạo/cập nhật sẽ được **Amazon Comprehend** tự động phân tích để gợi ý mức độ ưu tiên — thay thế workshop EC2 đơn giản trong kế hoạch ban đầu và đáp ứng CLO3.

## Kiến trúc

> **[Sơ đồ — chưa chèn ảnh]:** user → CloudFront + S3 (frontend) → EC2 Spring Boot API (public subnet) → RDS MySQL (private subnet); EC2 còn gọi Amazon Comprehend qua IAM Role — tất cả trong một VPC.

## Các thành phần chính

- **Frontend:** HTML/CSS/JavaScript thuần, triển khai trên **S3 + CloudFront**.
- **Backend:** REST API Java Spring Boot trên **EC2** (public subnet của VPC).
- **Database:** MySQL trên **Amazon RDS** (private subnet), chỉ nhận kết nối từ Security Group của EC2.
- **AI service:** **Amazon Comprehend** được EC2 gọi qua IAM Role (không hardcode Access Key) để phân tích sentiment và trích xuất từ khóa từ mô tả task.

## Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| Ngôn ngữ lập trình | Java 17 |
| Framework Backend | Spring Boot 3.3, Spring Security, Spring Data JPA |
| Xác thực | JWT (JSON Web Token), mã hóa mật khẩu BCrypt |
| Cơ sở dữ liệu | MySQL 8.0 (Amazon RDS) |
| Dịch vụ AI | Amazon Comprehend (DetectSentiment, DetectKeyPhrases) |
| Frontend | HTML5, CSS3, JavaScript thuần (Fetch API) |
| Đóng gói & triển khai | Docker, Docker Compose |
| Hạ tầng Cloud | Amazon EC2, Amazon RDS, Amazon VPC, IAM Role |
| Công cụ build | Apache Maven |
| Công cụ kiểm thử API | Postman, curl |

## Thiết kế cơ sở dữ liệu

Hệ thống sử dụng 3 bảng chính: `users`, `projects`, `tasks`. Bảng `tasks` có thêm 2 cột phục vụ tính năng AI: `priority` (`LOW`/`MEDIUM`/`HIGH`, do AI gợi ý) và `ai_key_phrases` (các từ khóa do Comprehend trích xuất).

Quan hệ: một user sở hữu nhiều project (**1–N**); một project chứa nhiều task (**1–N**); một task có thể được gán cho một user (`assignee`, quan hệ **N–1**).

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** sơ đồ quan hệ thực thể (ERD) 3 bảng users / projects / tasks (vẽ bằng draw.io).