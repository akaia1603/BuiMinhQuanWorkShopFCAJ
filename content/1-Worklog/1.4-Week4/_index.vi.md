---
title: "Worklog Tuần 4"
date: 2026-08-15
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Bắt đầu dự án capstone fighting-game và prototype cơ chế game.
* Hoàn thiện mô hình game trên LeopardJS và bắt đầu Authentication với netcode.

**Thời gian:** 15/08/2026 – 21/08/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Tham dự kickoff dự án: tổng quan kiến trúc, phân vai, deliverable <br> - Xác định yêu cầu game: đối kháng 2 người, matchmaking, triển khai cloud | 17/08/2026 | 17/08/2026 | Brief dự án FCAJ |
| 3 | - **Prototype:** Xây game đối kháng cơ bản trên Scratch (di chuyển, tấn công, máu), gồm hit detection và điều kiện thắng/thua | 18/08/2026 | 18/08/2026 | Scratch editor |
| 4 | - Chuyển logic game từ Scratch sang cấu trúc project LeopardJS <br> - Triển khai sprite nhân vật, animation và xử lý input | 19/08/2026 | 19/08/2026 | Tài liệu LeopardJS |
| 5 | - Chạy và kiểm thử game local; sửa lỗi render và va chạm | 20/08/2026 | 20/08/2026 | |
| 6 | - Học kiến trúc netcode: WebSocket, player slot, đồng bộ trạng thái <br> - **Phác thảo:** Thiết kế luồng auth (login → session → tham gia trận) và tích hợp hook auth ban đầu | 21/08/2026 | 21/08/2026 | |

### Kết quả đạt được tuần 4:

* Tham gia dự án capstone fighting-game với vai trò thành viên tích cực.
* Xây prototype Scratch chơi được: di chuyển, tấn công, nhận sát thương, thắng ván.
* Xác nhận cơ chế game trước khi đầu tư hạ tầng cloud và netcode.
* Chuyển thành công prototype Scratch sang LeopardJS và chạy trên máy phát triển.
* Triển khai gameplay cốt lõi: hai nhân vật, combo tấn công, thanh máu và kết quả ván đấu.
* Hiểu mô hình multiplayer real-time qua WebSocket và chuẩn bị codebase client cho CI/CD.
