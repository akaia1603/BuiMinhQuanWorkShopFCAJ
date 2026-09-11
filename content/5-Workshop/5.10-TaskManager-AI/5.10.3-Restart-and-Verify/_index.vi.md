---
title: "Khởi động lại & kiểm thử"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.10.3.</b> "
---

## Bước 3 — Khởi động lại & kiểm thử

1. Khởi động lại service backend để AWS SDK nhận quyền mới: `sudo systemctl restart taskmanager`.
2. Tạo task với mô tả có sắc thái khẩn cấp (vd: "Cần sửa gấp lỗi nghiêm trọng trước hạn nộp").

![Response tạo task với priority do AI gợi ý](/images/5-Workshop/5.10-TaskManager-AI/06-ai-priority-response.png)

*Response tạo task với `priority = HIGH` và `aiKeyPhrases` được điền tự động.*

## Kết quả mong đợi

- Response tạo task trả về `priority = HIGH` và `aiKeyPhrases` chứa các cụm từ khóa do Comprehend trích xuất
- Không có bất kỳ access key nào trong code — quyền lấy từ instance role