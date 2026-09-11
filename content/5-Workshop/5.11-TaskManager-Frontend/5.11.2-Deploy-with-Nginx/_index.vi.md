---
title: "Deploy bằng Nginx"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.11.2.</b> "
---

## Bước 2 — Deploy frontend bằng Nginx trên EC2

1. Cài Nginx trên EC2: `sudo yum install -y nginx`.

![Cài Nginx trên EC2](/images/5-Workshop/5.11-TaskManager-Frontend/02-nginx-install.png)

*Nginx đã được cài trên EC2.*

2. Copy toàn bộ thư mục `frontend/` vào `/usr/share/nginx/html/`, tạo server block trong `/etc/nginx/conf.d/taskmanager.conf` (listen **80**, `root /usr/share/nginx/html`, `try_files $uri $uri/ /index.html;`).

![Cấu hình server block Nginx](/images/5-Workshop/5.11-TaskManager-Frontend/03-nginx-conf.png)

*Server block trong `taskmanager.conf`.*

3. Khởi động và bật tự chạy: `sudo systemctl start nginx && sudo systemctl enable nginx`.
4. Mở **port 80** trong Security Group của EC2 (Custom TCP, source `0.0.0.0/0`).

![Security Group mở port 80](/images/5-Workshop/5.11-TaskManager-Frontend/04-sg-port80.png)

*Port 80 mở cho HTTP trong Security Group của EC2.*

> **Ghi chú lựa chọn:** dùng Nginx trên cùng EC2 với backend giúp frontend/backend gần nhau và tiết kiệm chi phí cho project quy mô nhỏ; phương án **S3 + CloudFront** đã được thực hành riêng ở mục [5.4](../5.4-S3-CloudFront).