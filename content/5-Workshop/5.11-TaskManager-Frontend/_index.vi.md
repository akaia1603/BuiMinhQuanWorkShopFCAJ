---
title: "Task Manager — frontend & kiểm thử end-to-end"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Mục tiêu

Đưa giao diện Task Manager lên web (qua HTTP port 80, sẵn sàng nâng cấp HTTPS bằng Let's Encrypt) và kiểm thử toàn bộ hệ thống end-to-end, kể cả gợi ý mức độ ưu tiên của AI.

## Các mục con

1. [Trỏ frontend tới API](5.11.1-Point-Frontend-to-API/) — đặt biến `API_BASE` trong `frontend/js/config.js`.
2. [Deploy bằng Nginx](5.11.2-Deploy-with-Nginx/) — cài đặt, server block, mở port 80 trong Security Group.
3. [Kiểm thử end-to-end](5.11.3-End-to-End-Test/) — đăng ký, tạo project, task, priority AI.
4. [Chức năng & kết quả mong đợi](5.11.4-Features-and-Outcome/) — danh sách tính năng và tiêu chí thành công.
5. [Troubleshooting](5.11.5-Troubleshooting/) — lỗi quyền, CSS và JWT.