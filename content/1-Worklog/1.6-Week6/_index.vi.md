---
title: "Worklog Tuần 6"
date: 2026-08-29
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Tích hợp dịch vụ AI (Amazon Comprehend) vào backend Task Manager qua IAM Role.
* Triển khai frontend trên S3 + CloudFront, kiểm thử end-to-end và tài liệu hóa việc dọn dẹp tài nguyên.

**Thời gian:** 29/08/2026 – 04/09/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Tạo IAM role `taskmanager-ec2-comprehend-role` với policy `ComprehendReadOnly` <br> - Gắn role vào EC2 instance và restart systemd service | 31/08/2026 | 31/08/2026 | Tài liệu AWS IAM |
| 3 | - Triển khai `AiAnalysisService` trong backend (DetectSentiment, DetectKeyPhrases) <br> - **Kiểm thử:** tạo task với từ ngữ khẩn cấp → kỳ vọng `priority = HIGH` + `aiKeyPhrases` | 01/09/2026 | 01/09/2026 | Tài liệu Amazon Comprehend |
| 4 | - Trỏ frontend `API_BASE` tới endpoint EC2 và upload site lên S3 <br> - Tạo CloudFront Distribution cho frontend | 02/09/2026 | 02/09/2026 | |
| 5 | - **Kiểm thử E2E:** đăng ký → tạo project/task → AI priority → đổi trạng thái → xóa <br> - Ghi lại các bước dọn dẹp (RDS, EC2, CloudFront, S3, API Gateway, Lambda, DynamoDB, VPC, IAM) | 03/09/2026 | 03/09/2026 | |
| 6 | - Xác minh đầy đủ chức năng (CRUD + assignee + AI) và hoàn thiện bài lab workshop | 04/09/2026 | 04/09/2026 | |

### Kết quả đạt được tuần 6:

* Tích hợp Amazon Comprehend không cần hardcode credentials bất kỳ — quyền lấy từ instance IAM Role.
* Xác minh AI gợi ý mức ưu tiên và trích xuất từ khóa khi tạo/cập nhật task.
* Triển khai frontend JS thuần lên S3 + CloudFront và kiểm thử toàn hệ thống end-to-end qua trình duyệt.
* Hoàn thiện bộ chức năng: JWT auth, CRUD project/task, cập nhật trạng thái, assignee và AI insights.
* Ghi lại hướng dẫn dọn dẹp tài nguyên kèm screenshot phục vụ báo cáo cuối kỳ.