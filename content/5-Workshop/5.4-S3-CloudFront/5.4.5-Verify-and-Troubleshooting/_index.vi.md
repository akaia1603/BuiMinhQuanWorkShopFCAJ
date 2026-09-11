---
title: "Xác minh & troubleshooting"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.4.5.</b> "
---

## Bước 5 — Kiểm thử

1. Đợi Distribution chuyển sang trạng thái **Enabled**.
2. Mở **Distribution domain name** trên trình duyệt để kiểm thử.

![Trang web tải thành công qua CloudFront HTTPS](/images/5-Workshop/5.4-S3-CloudFront/09-site-https.png)

*Trình duyệt hiển thị thành công trang web qua link CloudFront (có ổ khóa HTTPS).*

## Kết quả mong đợi

- Website tĩnh truy cập được qua link CloudFront với ổ khóa HTTPS
- Quyền đọc công khai chỉ cấp qua bucket policy (không đổi ACL từng object)

## Troubleshooting

| Vấn đề | Kiểm tra |
|--------|----------|
| Mở URL báo "Access Denied" | Xác nhận bucket policy cho phép `s3:GetObject` công khai và tên index document trùng khớp |
| CloudFront vẫn "In Progress" | Chờ vài phút cho Distribution chuyển sang **Enabled** |