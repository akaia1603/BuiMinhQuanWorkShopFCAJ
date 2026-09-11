---
title: "Thứ tự thực hiện, kỹ năng & checklist"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.1.3.</b> "
---

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