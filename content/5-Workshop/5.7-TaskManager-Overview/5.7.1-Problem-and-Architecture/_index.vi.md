---
title: "Bài toán & kiến trúc"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.7.1.</b> "
---

## Mục đích

Workshop này ghi lại toàn bộ thực hành AWS đã triển khai trong đợt thực tập FCAJ theo trình tự: chuẩn bị môi trường, giám sát chi phí, các workshop nền tảng về serverless và mạng, rồi tới dự án chính — **Task Manager API**, backend Java Spring Boot hoàn chỉnh trên **EC2 + RDS**, tích hợp AI **Amazon Comprehend** để tự động gợi ý mức độ ưu tiên cho task (đáp ứng CLO3).

Mỗi mục đều ghi rõ các bước thao tác trên AWS Console và kèm ảnh chụp màn hình tại mọi điểm cần minh chứng cho báo cáo.

## Mô tả bài toán

Task Manager API là REST API backend phục vụ quản lý công việc/dự án ở quy mô nhỏ: người dùng đăng ký/đăng nhập, tạo và quản lý các **Project**, tạo/quản lý các **Task** thuộc từng project với trạng thái `TODO`, `IN_PROGRESS`, `DONE`. Mỗi task khi tạo/cập nhật sẽ được **Amazon Comprehend** tự động phân tích để gợi ý mức độ ưu tiên — thay thế workshop EC2 đơn giản trong kế hoạch ban đầu và đáp ứng CLO3.

## Kiến trúc

![Kiến trúc tổng thể Task Manager](/images/5-Workshop/5.7-TaskManager-Overview/01-architecture.jpg)

*Sơ đồ: user → Nginx trên EC2 (frontend, port 80) → Spring Boot API (port 8080) → RDS MySQL (private subnet); EC2 còn gọi Amazon Comprehend qua IAM Role — tất cả trong một VPC.*

> Frontend được phục vụ bởi Nginx chạy trên cùng EC2 với backend; phương án **S3 + CloudFront** đã được thực hành riêng ở mục [5.4](../5.4-S3-CloudFront).