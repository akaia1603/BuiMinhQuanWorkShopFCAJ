---
title: "Chuẩn bị môi trường & Region"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

## Mục tiêu

Chuẩn bị tài khoản AWS và thống nhất một Region trước khi triển khai bất kỳ dịch vụ nào, tránh lỗi kết nối chéo vùng.

## Điều kiện tiên quyết

- Tài khoản AWS hoặc IAM User đủ quyền thao tác trên S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch, IAM
- Trình duyệt web (Chrome / Firefox / Edge)
- Postman hoặc curl để kiểm thử API
- JDK 17, Maven, Docker cài trên máy cá nhân (build/test trước khi deploy)

## Các mục con

1. [Đăng nhập Console](5.2.1-Sign-in-to-Console/) — đăng nhập vào AWS.
2. [Chọn Region](5.2.2-Select-Region/) — chọn `ap-southeast-1`.
3. [Xác minh & troubleshooting](5.2.3-Verify-and-Troubleshooting/) — kết quả mong đợi và lỗi thường gặp.