---
title: "Xác minh & troubleshooting"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.9.4.</b> "
---

## Kết quả mong đợi

- Backend chạy dưới dạng systemd service, tự khởi động khi reboot
- `POST /api/auth/register` trả về JWT token
- `GET /actuator/health` trả về `{"status":"UP"}` khi kiểm tra bằng `curl`

![POST /api/auth/register trả về JWT token](/images/5-Workshop/5.9-TaskManager-EC2/06-register-jwt.png)

*Kết quả gọi `POST /api/auth/register` trả về JWT token.*

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| EC2 không kết nối được RDS | Kiểm tra inbound rule của Security Group RDS cho port 3306 — source phải là Security Group của EC2, không mở public |
| Đăng nhập báo `403`, log hiện `SignatureException: JWT signature does not match` | `JWT_SECRET` trong `app.env` quá ngắn (< 32 ký tự). Đổi thành chuỗi ≥ 32 ký tự rồi restart service |
| Backend chạy nhưng không đúng cấu hình (token tạo ra bị từ chối) | Các property trong code nằm dưới prefix `app.*` (ví dụ `@Value("${app.jwt.secret}")`). Khi chạy `java -jar` phải truyền `--app.jwt.secret`, `--app.aws.region`, `--app.ai.enabled` — không phải `--jwt.secret`, `--aws.region`, `--ai.enabled` |
| App báo `Unknown database 'taskmanager'` khi khởi động | Database chưa được tạo trên RDS — xem Troubleshooting tại [5.8.3](../5.8-TaskManager-RDS/5.8.3-Verify-and-Troubleshooting) |