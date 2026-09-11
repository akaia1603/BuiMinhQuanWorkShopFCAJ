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

![Sơ đồ kiến trúc serverless notes API](/images/5-Workshop/5.5-Serverless-API/01-diagram.png)

*Sơ đồ: client → API Gateway → Lambda → DynamoDB.*

## Các mục con

1. [Tạo bảng DynamoDB](5.5.1-Create-DynamoDB-Table/) — `fcaj-notes`.
2. [Tạo IAM Role cho Lambda](5.5.2-IAM-Role-for-Lambda/) — quyền execution cơ bản + truy cập DynamoDB.
3. [Tạo Lambda function](5.5.3-Create-Lambda-Function/) — Python 3.12, handler GET + POST.
4. [Tạo API Gateway](5.5.4-Create-API-Gateway/) — HTTP API với `GET /notes` và `POST /notes`.
5. [Kiểm thử API](5.5.5-Test-Notes-API/) — GET/POST trên Postman.
6. [Kết quả mong đợi](5.5.6-Expected-Outcome/) — tổng kết kết quả serverless.