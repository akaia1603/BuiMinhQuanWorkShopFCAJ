---
title: "Bản đề xuất"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Task Manager API — Backend Full-Stack tích hợp AI trên AWS

## Ứng dụng Java Spring Boot hoàn chỉnh trên EC2 + RDS với Amazon Comprehend

---

### 1. Tóm tắt điều hành

Bản đề xuất này mô tả nội dung thực hành trọng tâm của đợt thực tập: xây dựng và triển khai backend REST hoàn chỉnh tên là **Task Manager API** trên AWS. Hệ thống cho phép người dùng đăng ký/đăng nhập, quản lý dự án và công việc, đồng thời dùng **Amazon Comprehend** (AI) để tự động phân tích mỗi mô tả task và gợi ý mức độ ưu tiên.

Chương trình còn gồm chuỗi workshop nền tảng trong cùng Region (`ap-southeast-1`): giám sát chi phí (Budgets + CloudWatch), website tĩnh (S3 + CloudFront), serverless notes API (Lambda + API Gateway + DynamoDB) và thiết kế VPC 2-tier. Các workshop này xây dựng kỹ năng nền tảng cho dự án chính.

---

### 2. Tuyên bố vấn đề

#### Vấn đề là gì?

Các nhóm nhỏ thường quản lý công việc bằng Excel hoặc công cụ nặng nề khó tùy chỉnh. Chưa có backend tự xây dựng vừa (1) quản lý dự án/công việc kèm xác thực chuẩn chỉnh, vừa (2) minh họa cách nhúng dịch vụ AI vào ứng dụng thông thường mà không hardcode credentials.

#### Giải pháp

Hệ thống full-stack triển khai trên AWS:

- **Frontend:** HTML/CSS/JS thuần host trên S3 + CloudFront (HTTPS).
- **Backend:** Java 17 + Spring Boot 3.3 (Spring Security JWT, Spring Data JPA) trên EC2.
- **Database:** MySQL 8.0 trên Amazon RDS trong private subnet.
- **AI:** Amazon Comprehend (DetectSentiment, DetectKeyPhrases) gọi qua IAM Role gắn với EC2 — không hardcode Access Key (đáp ứng CLO3).
- **Mạng:** VPC 2-tier (public subnet cho EC2, private subnet cho RDS).

#### Lợi ích

- **Triển khai full-stack thực tế:** mọi tầng của ứng dụng hiện đại được triển khai trên AWS an toàn.
- **Tích hợp AI an toàn:** IAM ít quyền nhất thay vì key tĩnh.
- **Kiểm soát chi phí:** AWS Budgets + CloudWatch billing alarm giữ mọi thứ trong Free Tier.
- **Tái lập được:** đóng gói Maven + Docker, cấu hình qua biến môi trường (`app.env`).

---

### 3. Kiến trúc giải pháp

Kiến trúc theo mô hình 3 tầng chuẩn trong một VPC:

- **Tầng client:** frontend tĩnh trên S3, phục vụ qua CloudFront bằng HTTPS.
- **Tầng ứng dụng:** EC2 (public subnet) chạy REST API Spring Boot cổng 8080.
- **Tầng dữ liệu:** RDS MySQL (private subnet), chỉ kết nối được từ Security Group của EC2 cổng 3306.
- **AI service:** Amazon Comprehend được EC2 gọi qua instance IAM Role.

Các workshop serverless tái sử dụng khái niệm mạng tương tự: notes API dùng API Gateway + Lambda + DynamoDB, website tĩnh dùng S3 + CloudFront — chung Region và chung cơ chế giám sát chi phí.

#### Dịch vụ AWS sử dụng

- **Amazon S3 + CloudFront:** hosting frontend tĩnh qua HTTPS
- **AWS Lambda + API Gateway + DynamoDB:** workshop serverless notes API
- **Amazon VPC, EC2, RDS:** mạng 2 tầng và runtime của dự án chính
- **IAM:** role/policy gồm instance role cấp quyền đọc Comprehend cho EC2
- **Amazon Comprehend:** phân tích sentiment và trích xuất từ khóa cho mức ưu tiên task
- **AWS Budgets + CloudWatch:** giám sát chi phí và billing alarm

---

### 4. Triển khai kỹ thuật

#### Các giai đoạn triển khai

1. **Giai đoạn 1: Môi trường & kiểm soát chi phí (Tuần 1–3)**  
   Tạo tài khoản AWS, chọn Region (`ap-southeast-1`), AWS Budgets + CloudWatch billing alarm.
2. **Giai đoạn 2: Workshop nền tảng (Tuần 4)**  
   Website tĩnh (S3 + CloudFront), serverless notes API (Lambda + API Gateway + DynamoDB).
3. **Giai đoạn 3: VPC 2-tier & dự án chính (Tuần 5)**  
   VPC/Subnet/IAM, RDS MySQL, backend Spring Boot trên EC2.
4. **Giai đoạn 4: Tích hợp AI & bàn giao (Tuần 6–7)**  
   Comprehend qua IAM Role, frontend + kiểm thử end-to-end, dọn dẹp, báo cáo.

#### Yêu cầu kỹ thuật

- **Backend:** Java 17, Spring Boot 3.3, Spring Security (JWT), Spring Data JPA
- **Build:** Maven (`mvn clean package -DskipTests`), Docker để đóng gói
- **Hạ tầng:** EC2 (Amazon Linux 2023, t2.micro), RDS MySQL `db.t3.micro`, VPC 2-tier, Security Group ít quyền nhất
- **AI:** AWS SDK for Java gọi DetectSentiment / DetectKeyPhrases
- **Bảo mật:** JWT + BCrypt, database private, phân quyền qua IAM Role (không key tĩnh)

---

### 5. Timeline & Milestone

- **Tuần 1–3:** AWS cơ bản, bảo mật tài khoản, lưu trữ/CLI, giám sát chi phí.
- **Tuần 4:** Workshop S3 + CloudFront và serverless notes API.
- **Tuần 5:** VPC 2-tier, RDS, backend Spring Boot deploy trên EC2.
- **Tuần 6:** Tích hợp AI Comprehend, frontend, kiểm thử end-to-end.
- **Tuần 7:** Dọn dẹp tài nguyên và nộp báo cáo cuối cùng.

---

### 6. Ước tính ngân sách

- **Ưu tiên Free Tier:** `t2.micro` / `db.t3.micro` và serverless on-demand nằm trong giới hạn miễn phí của AWS.
- **Giám sát chủ động:** AWS Budgets (`FCAJ-Budget`, 5 USD/tháng) cảnh báo 50%/80% cộng CloudWatch billing alarm.
- **Kỷ luật dọn dẹp:** teardown có tài liệu ngay sau khi nộp báo cáo.

---

### 7. Đánh giá rủi ro

| Rủi ro | Tác động | Xác suất | Giảm thiểu |
| --- | --- | --- | --- |
| RDS không kết nối được từ EC2 | Cao | Trung bình | Chỉ mở inbound 3306 với source là Security Group của EC2 |
| Chi phí vượt ngưỡng | Trung bình | Thấp | Budget + billing alarm cấu hình trước khi chạy dịch vụ tốn phí |
| Lỗi tích hợp AI / thiếu quyền | Trung bình | Thấp | IAM Role `ComprehendReadOnly` gắn vào instance; restart service sau khi đổi role |
| Lộ credentials | Cao | Thấp | Không hardcode Access Key bất kỳ đâu; cấu hình qua `app.env`/biến môi trường |

---

### 8. Kết quả mong đợi

- REST API Task Manager hoạt động với JWT auth, CRUD project/task và cập nhật trạng thái.
- AI gợi ý mức ưu tiên task và trích xuất từ khóa qua Amazon Comprehend.
- Triển khai an toàn trên AWS (database private, IAM ít quyền nhất, frontend HTTPS).
- Tài liệu workshop tái sử dụng được và tài khoản AWS sạch sau khi kết thúc.