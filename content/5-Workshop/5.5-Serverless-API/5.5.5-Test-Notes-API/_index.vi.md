---
title: "Kiểm thử notes API"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.5.5.</b> "
---

## Bước 5 — Kiểm thử

1. Gọi **GET /notes** (trả về mảng rỗng ban đầu).

![Item đã lưu vào DynamoDB](/images/5-Workshop/5.5-Serverless-API/09-dynamodb-item.png)

*Bảng DynamoDB có item vừa thêm.*

2. **POST /notes** với nội dung mẫu, gọi lại **GET /notes** để xác nhận dữ liệu đã lưu vào DynamoDB.

![Response của GET /notes trên Postman](/images/5-Workshop/5.5-Serverless-API/10-postman-get.png)

*Kết quả GET thành công trên Postman.*

![Response của POST /notes trên Postman](/images/5-Workshop/5.5-Serverless-API/11-postman-post.png)

*Kết quả POST thành công trên Postman.*