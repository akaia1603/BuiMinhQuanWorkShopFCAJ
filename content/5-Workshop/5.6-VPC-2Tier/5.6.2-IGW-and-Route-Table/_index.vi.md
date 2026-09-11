---
title: "Internet Gateway & route table"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.6.2.</b> "
---

## Bước 2 — Internet Gateway & route table

1. Tạo **Internet Gateway**, gắn vào VPC.

![Gắn Internet Gateway](/images/5-Workshop/5.6-VPC-2Tier/04-create-igw.png)

*Internet Gateway đã được gắn vào VPC.*

2. Tạo route table cho subnet Public, thêm route `0.0.0.0/0` → Internet Gateway, gán vào subnet Public.
3. Subnet Private giữ route table mặc định (không có đường ra internet).

![Cấu hình route table](/images/5-Workshop/5.6-VPC-2Tier/05-route-table.png)

*Route table với `0.0.0.0/0` → Internet Gateway.*