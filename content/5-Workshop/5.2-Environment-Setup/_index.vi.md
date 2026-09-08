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

## Bước 1 — Đăng nhập Console

1. Mở https://console.aws.amazon.com và đăng nhập tài khoản.

## Bước 2 — Chọn Region

1. Ở góc trên bên phải thanh điều hướng, chọn **Asia Pacific (Singapore) — `ap-southeast-1`** (hoặc region thống nhất theo hướng dẫn của chương trình FCAJ).
2. Toàn bộ dịch vụ trong báo cáo này đều triển khai cùng một region này.

## Kết quả mong đợi

- Đồng hồ region hiển thị `ap-southeast-1` ở mọi thao tác Console
- Riêng Billing Alarm vẫn dùng `us-east-1` (alarm là region-specific, xem [5.3](5.3-Cost-Monitoring/))

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** giao diện Console sau khi đã chuyển đúng Region `ap-southeast-1` (góc trên bên phải hiển thị tên region đã chọn).

## Troubleshooting

| Vấn đề | Kiểm tra |
|--------|----------|
| Tài nguyên tạo nhầm region khác | Xác nhận đồng hồ region góc trên bên phải trước mỗi thao tác |
| Gọi chéo dịch vụ bị lỗi | Các dịch vụ triển khai ở nhiều region — giữ tất cả tại `ap-southeast-1` |