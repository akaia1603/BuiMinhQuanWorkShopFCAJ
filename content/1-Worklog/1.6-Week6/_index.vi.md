---
title: "Worklog Tuần 6"
date: 2026-08-29
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Hoàn thành dự án capstone (xử lý sau trận bất đồng bộ, củng cố VPC).
* Hoàn thành nội dung workshop lab AWS.

**Thời gian:** 29/08/2026 – 04/09/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Triển khai xử lý sau trận bất đồng bộ: DynamoDB Streams → MatchAnalytics Lambda | 31/08/2026 | 31/08/2026 | |
| 3 | - Chuyển MatchMaker Lambda sang private subnet với VPC endpoints (không NAT); cài CodeDeploy agent trên EC2 fleet | 01/09/2026 | 01/09/2026 | |
| 4 | - Kiểm thử tích hợp cuối: matchmaking → gameplay → kết thúc trận → analytics | 02/09/2026 | 02/09/2026 | |
| 5 | - Hoàn thành các phần workshop: S3 VPC endpoints, mô phỏng on-prem, cleanup (ghi lại kèm screenshot, hủy trước khi xóa) | 03/09/2026 | 03/09/2026 | Template workshop FCAJ |
| 6 | - Hoàn thành deliverable capstone và handoff tài liệu lab workshop cho team | 04/09/2026 | 04/09/2026 | |

### Kết quả đạt được tuần 6:

* Triển khai pipeline **Flow E**: DynamoDB Stream `ActiveMatches` → Lambda `FightingGameMatchAnalytics` → bảng `MatchAnalytics`.
* Cấu hình lại MatchMaker trong private subnet với DynamoDB gateway và EC2/CloudWatch interface endpoints.
* Cài và cấu hình CodeDeploy agent trên game server instance.
* Xác minh vòng đời game đầy đủ: login → hàng đợi → trận → WebSocket gameplay → ghi nhận trận kết thúc trong DynamoDB.
* Hoàn thành toàn bộ bài lab workshop gồm VPC Gateway endpoints, PrivateLink interface endpoints và mô phỏng DNS.
* Ghi lại screenshot teardown (chỉ màn hình xác nhận, không xóa thật).
