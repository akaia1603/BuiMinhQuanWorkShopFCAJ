---
title: "Task Manager — triển khai EC2 & backend"
date: 2026-09-01
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

## Mục tiêu

Triển khai backend Java Spring Boot trên EC2 trong cùng VPC với RDS, đồng thời chỉ cho instance này kết nối được database.

## Bước 1 — Khởi chạy EC2

1. Khởi chạy EC2 instance (**Amazon Linux 2023, t3.micro**) trong cùng VPC với RDS, ở public subnet.
2. Security Group: mở **port 22 (nguồn: My IP)** và **port 8080 (nguồn: Anywhere)** (mở thêm **port 80** khi deploy frontend ở mục [5.11](5.11-TaskManager-Frontend/)).

## Bước 2 — Cho phép EC2 kết nối RDS

1. Vào Security Group của RDS `rds-sg` → **Edit inbound rules**.
2. Thêm rule **MYSQL/Aurora (port 3306)**, Source: **Security Group của EC2** (không mở Anywhere).

## Bước 3 — Cài Java và deploy

1. SSH vào EC2.
2. Cài Java 17: `sudo dnf install -y java-17-amazon-corretto-devel`.
3. Build trên máy local: `mvn clean package -DskipTests`, copy file `.jar` lên EC2 bằng `scp`.
4. Tạo file `app.env` chứa các biến môi trường: `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `AWS_REGION`, `AI_ENABLED` (`JWT_SECRET` phải dài **tối thiểu 32 ký tự**).
5. Tạo `systemd` service để ứng dụng tự khởi động lại khi EC2 reboot.
6. Khởi động service và theo dõi log: `journalctl -u taskmanager -f`.

## Kết quả mong đợi

- Backend chạy dưới dạng systemd service, tự khởi động khi reboot
- `POST /api/auth/register` trả về JWT token
- `GET /actuator/health` trả về `{"status":"UP"}` khi kiểm tra bằng `curl`

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| EC2 không kết nối được RDS | Kiểm tra inbound rule của Security Group RDS cho port 3306 — source phải là Security Group của EC2, không mở public |
| Đăng nhập báo `403`, log hiện `SignatureException: JWT signature does not match` | `JWT_SECRET` trong `app.env` quá ngắn (< 32 ký tự). Đổi thành chuỗi ≥ 32 ký tự rồi restart service |
| Backend chạy nhưng không đúng cấu hình (token tạo ra bị từ chối) | Các property trong code nằm dưới prefix `app.*` (ví dụ `@Value("${app.jwt.secret}")`). Khi chạy `java -jar` phải truyền `--app.jwt.secret`, `--app.aws.region`, `--app.ai.enabled` — không phải `--jwt.secret`, `--aws.region`, `--ai.enabled` |
| App báo `Unknown database 'taskmanager'` khi khởi động | Database chưa được tạo trên RDS — xem Troubleshooting mục [5.8](5.8-TaskManager-RDS/) |

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) EC2 instance ở trạng thái Running; (2) log service hiển thị dòng "Started TaskManagerApiApplication"; (3) kết quả gọi `POST /api/auth/register` trả về JWT token.