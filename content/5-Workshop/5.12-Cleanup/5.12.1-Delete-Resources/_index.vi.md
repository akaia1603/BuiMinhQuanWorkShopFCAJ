---
title: "Xóa các tài nguyên"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.12.1.</b> "
---

## Các bước

- **RDS:** **Stop** hoặc **Delete** instance `taskmanager-db` (lưu ý: Stop chỉ tạm dừng tối đa 7 ngày, sau đó AWS tự khởi động lại).

![Xóa RDS instance](/images/5-Workshop/5.12-Cleanup/01-rds-delete.png)

*Đang xóa instance `taskmanager-db`.*

- **EC2:** **Terminate** các instance đã dùng cho workshop VPC và Task Manager API.

![Terminate các EC2 instance](/images/5-Workshop/5.12-Cleanup/02-ec2-terminate.png)

*Đang terminate các EC2 instance.*

- **CloudFront + S3:** **Disable** rồi **Delete** Distribution; xóa nội dung và **Delete** S3 bucket.

![Disable CloudFront Distribution](/images/5-Workshop/5.12-Cleanup/03-cloudfront-delete.png)

*Đang disable CloudFront Distribution.*

![Xóa S3 bucket](/images/5-Workshop/5.12-Cleanup/04-s3-delete.png)

*Đang xóa S3 bucket.*

- **Lambda + API Gateway + DynamoDB:** Xóa Lambda function, xóa API Gateway, xóa bảng DynamoDB `fcaj-notes`.

![Xóa Lambda và API Gateway](/images/5-Workshop/5.12-Cleanup/05-lambda-apigw-delete.png)

*Đang xóa Lambda function và API Gateway.*

![Xóa bảng DynamoDB](/images/5-Workshop/5.12-Cleanup/06-dynamodb-delete.png)

*Đang xóa bảng DynamoDB `fcaj-notes`.*

- **IAM Role:** có thể giữ lại (không phát sinh phí) hoặc xóa nếu không còn dùng.
- Cuối cùng kiểm tra lại trang **Billing Dashboard** để xác nhận không còn tài nguyên nào phát sinh chi phí.