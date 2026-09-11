---
title: "Tạo Lambda function"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.5.3.</b> "
---

## Bước 3 — Lambda function

1. Tạo Lambda function `fcaj-notes-api`, Runtime **Python 3.12**, gắn IAM Role vừa tạo.

![Tạo Lambda function](/images/5-Workshop/5.5-Serverless-API/05-lambda-create.png)

*Trang tạo Lambda function.*

2. Viết mã xử lý 2 method — **GET** (liệt kê note) và **POST** (thêm note mới) — rồi **Deploy**.

![Mã nguồn Lambda](/images/5-Workshop/5.5-Serverless-API/06-lambda-code.png)

*Mã nguồn Lambda function.*