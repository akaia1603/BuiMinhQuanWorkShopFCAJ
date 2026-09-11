---
title: "Cài Java & deploy"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.9.3.</b> "
---

## Bước 3 — Cài Java và deploy

1. SSH vào EC2.
2. Cài Java 17: `sudo dnf install -y java-17-amazon-corretto-devel`.

![Cài Java 17 trên EC2](/images/5-Workshop/5.9-TaskManager-EC2/04-install-java.png)

*Java 17 đã được cài trên EC2 instance.*

3. Build trên máy local: `mvn clean package -DskipTests`, copy file `.jar` lên EC2 bằng `scp`.
4. Tạo file `app.env` chứa các biến môi trường: `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `AWS_REGION`, `AI_ENABLED` (`JWT_SECRET` phải dài **tối thiểu 32 ký tự**).
5. Tạo `systemd` service để ứng dụng tự khởi động lại khi EC2 reboot.
6. Khởi động service và theo dõi log: `journalctl -u taskmanager -f`.

![Log service backend](/images/5-Workshop/5.9-TaskManager-EC2/05-backend-log.png)

*Log service hiển thị dòng "Started TaskManagerApiApplication".*