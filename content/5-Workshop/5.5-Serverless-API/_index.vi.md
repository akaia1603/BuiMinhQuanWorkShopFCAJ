---
title: "Serverless API — Lambda + API Gateway + DynamoDB"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

## Mục tiêu

Xây dựng API ghi chú hoàn toàn serverless: API Gateway → Lambda → DynamoDB, không cần quản lý server.

## Kiến trúc

> **[Sơ đồ — chưa chèn ảnh]:** client → API Gateway → Lambda → DynamoDB.

## Bước 1 — Bảng DynamoDB

1. Tạo bảng `fcaj-notes`, Partition key: `id` (String), giữ nguyên Default settings (on-demand).

## Bước 2 — IAM Role cho Lambda

1. Tạo IAM Role cho Lambda với 2 policy: `AWSLambdaBasicExecutionRole` và `AmazonDynamoDBFullAccess`.

## Bước 3 — Lambda function

1. Tạo Lambda function `fcaj-notes-api`, Runtime **Python 3.12**, gắn IAM Role vừa tạo.
2. Viết mã xử lý 2 method — **GET** (liệt kê note) và **POST** (thêm note mới) — rồi **Deploy**.

## Bước 4 — API Gateway

1. Tạo **HTTP API**, tích hợp với Lambda function.
2. Cấu hình 2 route: **GET /notes** và **POST /notes**.

## Bước 5 — Kiểm thử

1. Gọi **GET /notes** (trả về mảng rỗng ban đầu).
2. **POST /notes** với nội dung mẫu, gọi lại **GET /notes** để xác nhận dữ liệu đã lưu vào DynamoDB.

## Kết quả mong đợi

- GET/POST trả về JSON và DynamoDB lưu được note
- Không có server phải quản lý — toàn bộ serverless

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) bảng DynamoDB có item vừa thêm; (2) mã nguồn Lambda function; (3) danh sách route trên API Gateway; (4) kết quả gọi GET/POST thành công trên Postman (response JSON).