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

> **[Sơ đồ — chưa chèn ảnh]:** user → CloudFront → S3 bucket.

## Bước 1 — Tạo S3 bucket

1. Tạo S3 bucket (tên duy nhất toàn cầu) tại `ap-southeast-1`.
2. Bỏ tick **Block all public access** để cho phép truy cập công khai.

## Bước 2 — Upload và bật static hosting

1. Upload file `index.html` lên bucket.
2. **Properties → Static website hosting → Enable**, Index document: `index.html`.

## Bước 3 — Bucket policy

1. **Permissions → Bucket policy**, thêm policy cho phép `s3:GetObject` công khai trên toàn bộ object.

## Bước 4 — CloudFront Distribution

1. Tạo **CloudFront Distribution**, Origin domain trỏ về bucket vừa tạo.
2. Viewer protocol policy: **Redirect HTTP to HTTPS**.

## Bước 5 — Kiểm thử

1. Đợi Distribution chuyển sang trạng thái **Enabled**.
2. Mở **Distribution domain name** trên trình duyệt để kiểm thử.

## Kết quả mong đợi

- Website tĩnh truy cập được qua link CloudFront với ổ khóa HTTPS
- Quyền đọc công khai chỉ cấp qua bucket policy (không đổi ACL từng object)

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) trang cấu hình S3 bucket (Static website hosting: Enabled); (2) CloudFront Distribution ở trạng thái Enabled; (3) trình duyệt hiển thị thành công trang web qua link CloudFront (có ổ khóa HTTPS).