---
title: "Task Manager — frontend & kiểm thử end-to-end"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Mục tiêu

Đưa giao diện Task Manager lên web qua HTTPS và kiểm thử toàn bộ hệ thống end-to-end, kể cả gợi ý mức độ ưu tiên của AI.

## Bước 1 — Trỏ frontend tới API

1. Sửa biến `API_BASE` trong `frontend/index.html` thành địa chỉ EC2 thật: `http://<EC2-Public-IP>:8080`.

## Bước 2 — Deploy lên S3 + CloudFront

1. Upload `index.html` lên S3 bucket, bật static website hosting, tạo CloudFront Distribution (lặp lại quy trình ở [5.4](5.4-S3-CloudFront/)).

## Bước 3 — Kiểm thử end-to-end

1. Truy cập qua link CloudFront.
2. Đăng ký tài khoản mới, tạo project, tạo task với nhiều nội dung khác nhau để quan sát AI gợi ý priority khác nhau, đổi trạng thái task, xóa task/project.

## Chức năng của hệ thống

- Đăng ký tài khoản mới, đăng nhập và nhận JWT token
- CRUD Project
- CRUD Task trong từng Project
- Cập nhật trạng thái Task (TODO / IN_PROGRESS / DONE)
- Gán Task cho một thành viên (assignee)
- Tự động gợi ý **Priority** + trích xuất từ khóa bằng AI (Amazon Comprehend) mỗi khi tạo/cập nhật task

## Kết quả mong đợi

- Mọi luồng thao tác hoạt động qua trình duyệt với backend thật
- Mỗi task hiển thị badge Priority và dòng "AI nhận diện: ..." bên dưới

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) giao diện đăng nhập/đăng ký trên frontend; (2) danh sách project; (3) danh sách task hiển thị badge Priority và dòng "AI nhận diện: ..." bên dưới mỗi task.