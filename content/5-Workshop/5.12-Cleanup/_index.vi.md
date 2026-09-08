---
title: "Dọn dẹp tài nguyên"
date: 2026-09-01
weight: 12
chapter: false
pre: " <b> 5.12. </b> "
---

## Mục tiêu

Loại bỏ toàn bộ tài nguyên đã tạo trong đợt thực tập để không phát sinh chi phí ngoài dự kiến sau khi hoàn thành — lý tưởng nhất là giữ cả tháng trong Free Tier.

## Các bước

- **RDS:** **Stop** hoặc **Delete** instance `taskmanager-db` (lưu ý: Stop chỉ tạm dừng tối đa 7 ngày, sau đó AWS tự khởi động lại).
- **EC2:** **Terminate** các instance đã dùng cho workshop VPC và Task Manager API.
- **CloudFront + S3:** **Disable** rồi **Delete** Distribution; xóa nội dung và **Delete** S3 bucket.
- **Lambda + API Gateway + DynamoDB:** Xóa Lambda function, xóa API Gateway, xóa bảng DynamoDB `fcaj-notes`.
- **IAM Role:** có thể giữ lại (không phát sinh phí) hoặc xóa nếu không còn dùng.
- Cuối cùng kiểm tra lại trang **Billing Dashboard** để xác nhận không còn tài nguyên nào phát sinh chi phí.

## Kết quả mong đợi

- Billing Dashboard sau khi dọn dẹp chỉ còn chi phí trong ngưỡng dự kiến/Free Tier

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** trang Billing Dashboard sau khi dọn dẹp cho thấy chi phí nằm trong ngưỡng dự kiến (tham khảo, không bắt buộc nếu Khoa không yêu cầu).