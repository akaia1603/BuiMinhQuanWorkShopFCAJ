---
title: "Worklog Tuần 3"
date: 2026-08-08
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Đi sâu vào các dịch vụ lưu trữ dữ liệu của AWS.
* Học giám sát hệ thống và quản lý tài nguyên bằng AWS CLI.

**Thời gian:** 08/08/2026 – 14/08/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Học S3 storage class, versioning và lifecycle policy <br> - Học EBS vs EFS: block vs file storage, use case | 10/08/2026 | 10/08/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Khám phá DynamoDB: bảng, partition, primary key, on-demand vs provisioned <br> - **Lab:** Tạo bảng DynamoDB, insert/query qua console và CLI | 11/08/2026 | 11/08/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Lab:** Cấu hình S3 versioning và thử khôi phục object | 12/08/2026 | 12/08/2026 | |
| 5 | - Học CloudWatch: metrics, alarm, logs, dashboard <br> - **Lab:** Tạo CloudWatch alarm cho CPU utilization của EC2 | 13/08/2026 | 13/08/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Cài đặt và cấu hình AWS CLI (access key, secret key, region mặc định) <br> - **Thực hành:** Quản lý tài nguyên EC2, S3, DynamoDB qua CLI | 14/08/2026 | 14/08/2026 | |

### Kết quả đạt được tuần 3:

* Tạo và truy vấn bảng DynamoDB; hiểu cơ bản về mô hình dữ liệu NoSQL.
* Cấu hình S3 versioning và lifecycle rule để bảo vệ dữ liệu.
* So sánh EBS, EFS và S3; xác định use case phù hợp cho từng loại.
* Tạo CloudWatch alarm và dashboard để giám sát tài nguyên đang chạy.
* Cài đặt AWS CLI và thực hiện thao tác CRUD trên EC2, S3, DynamoDB từ dòng lệnh.
* Thành thạo CLI — nền tảng cho tự động hóa và CI/CD ở các tuần sau.
* Xây dựng kiến thức lưu trữ áp dụng cho `MatchmakingQueue`, `ActiveMatches` và S3 bucket của dự án.
