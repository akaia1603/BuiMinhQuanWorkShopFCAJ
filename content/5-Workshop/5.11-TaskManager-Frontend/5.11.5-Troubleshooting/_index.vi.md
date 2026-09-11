---
title: "Troubleshooting"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.11.5.</b> "
---

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| Trang hiện ra nhưng CSS/JS không load (403) | Thư mục `css/`, `js/` có quyền `dr-x------` (500) — nginx không đọc được. Chạy `sudo chmod 755 /usr/share/nginx/html/css/ /usr/share/nginx/html/js/` rồi `sudo chmod 644 /usr/share/nginx/html/css/* /usr/share/nginx/html/js/*`, sau đó `sudo systemctl restart nginx` |
| Giao diện mất toàn bộ style, bố cục lỗi | File `style.css` bị lỗi cú pháp (selector `.stat-label` thiếu dấu `}`) làm trình duyệt bỏ qua phần CSS phía sau. Đã sửa đúng khối, kiểm tra bằng cách đếm `{`/`}` cân bằng |
| Gọi API trả về `403` sau khi đổi JWT secret | Token cũ trong trình duyệt không còn hợp lệ. Mở Console (F12) chạy `localStorage.clear()`, refresh lại trang và đăng nhập mới |