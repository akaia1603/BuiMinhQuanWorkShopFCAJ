---
title: "Website tĩnh — S3 + CloudFront"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

## Mục tiêu

Host website tĩnh (ví dụ frontend bundle) trên S3 và phục vụ qua CloudFront với giao thức HTTPS.

## Kiến trúc

![Sơ đồ kiến trúc S3 + CloudFront](/images/5-Workshop/5.4-S3-CloudFront/01-diagram.png)

*Sơ đồ: user → CloudFront → S3 bucket.*

## Các mục con

1. [Tạo S3 bucket](5.4.1-Create-S3-Bucket/) — tên duy nhất toàn cầu, cho phép đọc công khai.
2. [Bật static hosting](5.4.2-Enable-Static-Hosting/) — upload `index.html`, bật Static website hosting.
3. [Đặt bucket policy](5.4.3-Set-Bucket-Policy/) — `s3:GetObject` công khai.
4. [Tạo CloudFront Distribution](5.4.4-Create-CloudFront-Distribution/) — origin trỏ về bucket.
5. [Xác minh & troubleshooting](5.4.5-Verify-and-Troubleshooting/) — truy cập HTTPS qua CloudFront.