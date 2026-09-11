---
title: "Chức năng & kết quả mong đợi"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.11.4.</b> "
---

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
- Kiểm tra bằng `curl -I http://localhost/css/style.css` trả về `200 OK` (Content-Type: `text/css`)