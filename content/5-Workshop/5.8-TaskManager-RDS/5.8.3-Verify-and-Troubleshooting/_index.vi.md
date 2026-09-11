---
title: "Xác minh & troubleshooting"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.8.3.</b> "
---

## Kết quả mong đợi

- RDS instance `taskmanager-db` ở trạng thái `Available`
- Private — không mở public, chỉ cho kết nối từ Security Group của EC2
- Database `taskmanager` tồn tại và có thể kết nối bằng client (MySQL/MariaDB)

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| Backend không khởi động được, log báo `Unknown database 'taskmanager'` | Không đặt "Initial database name" lúc tạo RDS nên database chưa tồn tại. Cài client trên EC2: `sudo yum install -y mariadb105`, kết nối `mysql -h <endpoint> -u admin -p`, rồi tạo database: `CREATE DATABASE taskmanager; SHOW DATABASES;` |