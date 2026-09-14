---
title: "Tổng quan workshop & Task Manager API"
date: 2026-09-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

## Mục đích

Phần này ghi lại toàn bộ thực hành AWS đã triển khai trong đợt thực tập FCAJ theo trình tự: chuẩn bị môi trường, giám sát chi phí, các workshop nền tảng về serverless và mạng, rồi tới dự án chính — **Task Manager API**, backend Java Spring Boot hoàn chỉnh trên **EC2 + RDS**, tích hợp AI **Amazon Comprehend** để tự động gợi ý mức độ ưu tiên cho task (đáp ứng CLO3).

Mỗi mục đều ghi rõ các bước thao tác trên AWS Console và kèm ảnh chụp màn hình tại mọi điểm cần minh chứng cho báo cáo.

## Các mục con

1. [Mô tả bài toán & kiến trúc](5.7.1-Problem-and-Architecture/) — hệ thống làm gì, các thành phần liên kết ra sao và sơ đồ kiến trúc tổng thể.
2. [Thành phần & công nghệ](5.7.2-Components-and-Tech-Stack/) — frontend, backend, database, AI service và bảng công nghệ đầy đủ.
3. [Thiết kế cơ sở dữ liệu](5.7.3-Database-Design/) — các bảng `users` / `projects` / `tasks` và quan hệ giữa chúng.
4. [Điều kiện tiên quyết & Region](5.7.4-Prerequisites-and-Region/) — những gì cần chuẩn bị và chính sách dùng chung một region.
5. [Thứ tự thực hiện, kỹ năng & checklist](5.7.5-Order-and-Checklist/) — thứ tự đọc, kỹ năng và checklist xác minh cuối cùng.