---
title: "Điều kiện tiên quyết & Region"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.1.2.</b> "
---

## Điều kiện tiên quyết

- Tài khoản AWS quyền admin (hoặc IAM User đủ quyền trên S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch, IAM)
- Trình duyệt web (Chrome / Firefox / Edge)
- Công cụ kiểm thử API: Postman hoặc curl
- JDK 17, Maven, Docker cài trên máy cá nhân (build/test trước khi deploy)

## Region

Toàn bộ dịch vụ triển khai tại **`ap-southeast-1`** (Singapore) — mọi thứ nằm chung một region để tránh lỗi kết nối chéo vùng. Riêng Billing Alarm phải tạo tại **`us-east-1`** (xem [5.3](../5.3-Cost-Monitoring)).