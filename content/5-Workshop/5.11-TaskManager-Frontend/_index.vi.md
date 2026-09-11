---
title: "Task Manager — frontend & kiểm thử end-to-end"
date: 2026-09-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

## Mục tiêu

Đưa giao diện Task Manager lên web (qua HTTP port 80, sẵn sàng nâng cấp HTTPS bằng Let's Encrypt) và kiểm thử toàn bộ hệ thống end-to-end, kể cả gợi ý mức độ ưu tiên của AI.

## Bước 1 — Trỏ frontend tới API

1. Sửa biến `API_BASE` trong `frontend/js/config.js` thành địa chỉ EC2 thật: `http://<EC2-Public-IP>:8080`.

## Bước 2 — Deploy frontend bằng Nginx trên EC2

1. Cài Nginx trên EC2: `sudo yum install -y nginx`.
2. Copy toàn bộ thư mục `frontend/` vào `/usr/share/nginx/html/`, tạo server block trong `/etc/nginx/conf.d/taskmanager.conf` (listen **80**, `root /usr/share/nginx/html`, `try_files $uri $uri/ /index.html;`).
3. Khởi động và bật tự chạy: `sudo systemctl start nginx && sudo systemctl enable nginx`.
4. Mở **port 80** trong Security Group của EC2 (Custom TCP, source `0.0.0.0/0`).

> **Ghi chú lựa chọn:** dùng Nginx trên cùng EC2 với backend giúp frontend/backend gần nhau và tiết kiệm chi phí cho project quy mô nhỏ; phương án **S3 + CloudFront** đã được thực hành riêng ở mục [5.4](5.4-S3-CloudFront/).

## Bước 3 — Kiểm thử end-to-end

1. Truy cập qua `http://<EC2-Public-IP>`.
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
- Kiểm tra bằng `curl -I http://localhost/css/style.css` trả về `200 OK` (Content-Type: `text/css`)

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| Trang hiện ra nhưng CSS/JS không load (403) | Thư mục `css/`, `js/` có quyền `dr-x------` (500) — nginx không đọc được. Chạy `sudo chmod 755 /usr/share/nginx/html/css/ /usr/share/nginx/html/js/` rồi `sudo chmod 644 /usr/share/nginx/html/css/* /usr/share/nginx/html/js/*`, sau đó `sudo systemctl restart nginx` |
| Giao diện mất toàn bộ style, bố cục lỗi | File `style.css` bị lỗi cú pháp (selector `.stat-label` thiếu dấu `}`) làm trình duyệt bỏ qua phần CSS phía sau. Đã sửa đúng khối, kiểm tra bằng cách đếm `{`/`}` cân bằng |
| Gọi API trả về `403` sau khi đổi JWT secret | Token cũ trong trình duyệt không còn hợp lệ. Mở Console (F12) chạy `localStorage.clear()`, refresh lại trang và đăng nhập mới |

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) giao diện đăng nhập/đăng ký trên frontend; (2) danh sách project; (3) danh sách task hiển thị badge Priority và dòng "AI nhận diện: ..." bên dưới mỗi task.