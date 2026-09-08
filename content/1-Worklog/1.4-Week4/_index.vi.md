---
title: "Worklog Tuần 4"
date: 2026-08-15
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Thiết lập giám sát chi phí với AWS Budgets và CloudWatch billing alarm.
* Hoàn thành workshop website tĩnh (S3 + CloudFront) và workshop serverless notes API (Lambda + API Gateway + DynamoDB).

**Thời gian:** 15/08/2026 – 21/08/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Tạo budget `FCAJ-Budget` (Monthly, 5 USD) với cảnh báo 50% và 80% <br> - Bật Receive Billing Alerts (us-east-1) và tạo CloudWatch billing alarm (> 5 USD) | 17/08/2026 | 17/08/2026 | Tài liệu AWS Billing |
| 3 | - Tạo S3 bucket, upload `index.html`, bật static website hosting, thêm bucket policy public-read | 18/08/2026 | 18/08/2026 | Tài liệu AWS S3 |
| 4 | - Tạo CloudFront Distribution (HTTPS) trỏ tới bucket và kiểm thử truy cập | 19/08/2026 | 19/08/2026 | Tài liệu AWS CloudFront |
| 5 | - Tạo bảng DynamoDB `fcaj-notes` và IAM Role cho Lambda <br> - Viết Lambda `fcaj-notes-api` (Python 3.12) xử lý GET/POST | 20/08/2026 | 20/08/2026 | Tài liệu AWS Lambda |
| 6 | - Tạo HTTP API trên API Gateway với route `GET /notes` và `POST /notes` <br> - **Kiểm thử:** gọi GET/POST qua Postman và xác nhận dữ liệu lưu vào DynamoDB | 21/08/2026 | 21/08/2026 | |

### Kết quả đạt được tuần 4:

* Cấu hình AWS Budgets và CloudWatch billing alarm trước khi triển khai dịch vụ tốn phí — mọi thứ trong Free Tier.
* Host website tĩnh trên S3 và phục vụ qua CloudFront bằng HTTPS.
* Xây dựng và kiểm thử serverless notes API hoàn chỉnh: API Gateway → Lambda → DynamoDB.
* Có thực hành IAM Role cho Lambda và định tuyến HTTP API.
* Củng cố kỹ năng AWS CLI/DynamoDB từ các tuần trước thành luồng serverless end-to-end hoạt động.