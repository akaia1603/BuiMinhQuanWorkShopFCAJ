---
title: "Task Manager — tích hợp AI Amazon Comprehend"
date: 2026-09-01
weight: 10
chapter: false
pre: " <b> 5.10. </b> "
---

## Mục tiêu

Đáp ứng CLO3: tích hợp AI (Amazon Comprehend) vào backend. Thay vì hardcode Access Key / Secret Key — vốn không an toàn — hệ thống được cấp quyền gọi Comprehend thông qua **IAM Role gắn trực tiếp vào EC2 instance**, theo đúng thực hành chuẩn của AWS.

## Các mục con

1. [Tạo IAM Role](5.10.1-Create-IAM-Role/) — trust entity EC2, policy `ComprehendReadOnly`, tên `taskmanager-ec2-comprehend-role`.
2. [Gắn role vào EC2](5.10.2-Attach-Role-to-EC2/) — Modify IAM role + xác minh qua IMDSv2.
3. [Khởi động lại & kiểm thử](5.10.3-Restart-and-Verify/) — kiểm tra `priority` và `aiKeyPhrases` trong response.
4. [Troubleshooting & code minh họa](5.10.4-Troubleshooting-and-Code/) — lỗi kích hoạt dịch vụ và trích đoạn `AiAnalysisService`.