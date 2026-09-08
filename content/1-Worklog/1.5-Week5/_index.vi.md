---
title: "Worklog Tuần 5"
date: 2026-08-22
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Handoff client kèm luồng login cho team và triển khai CI/CD bằng GitHub Actions.
* Triển khai IAM Permission Boundaries và kiểm tra khả năng deploy của CodeDeploy.

**Thời gian:** 22/08/2026 – 28/08/2026

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Hoàn thiện UI login client và xử lý session; handoff codebase kèm tài liệu interface auth + netcode | 24/08/2026 | 24/08/2026 | |
| 3 | - Thiết lập cấu trúc repository GitHub và tạo workflow GitHub Actions ban đầu cho build và deploy <br> - Cấu hình S3 static website hosting cho browser client và kiểm thử deploy tự động đầu tiên | 25/08/2026 | 25/08/2026 | Tài liệu GitHub Actions |
| 4 | - Học IAM Permission Boundaries và mô hình deploy least-privilege <br> - Đăng ký GitHub OIDC identity provider trong IAM (không dùng access key cố định) | 26/08/2026 | 26/08/2026 | Tài liệu AWS IAM |
| 5 | - Tạo deploy role với trust policy giới hạn theo repo GitHub; gắn permissions <br> - Cấu hình repository secrets (`AWS_ROLE_ARN`, `COGNITO_*`, `ASSETS_BUCKET`, v.v.) | 27/08/2026 | 27/08/2026 | |
| 6 | - **Kiểm thử:** Push lên GitHub → xác minh S3 sync, Lambda update và CodeDeploy thành công | 28/08/2026 | 28/08/2026 | |

### Kết quả đạt được tuần 5:

* Bàn giao gói client hoạt động với luồng login và stub netcode cho team.
* Tạo repository dự án, thiết lập quy ước nhánh và triển khai workflow GitHub Actions đầu tiên.
* Tạo S3 assets bucket với static website hosting, bucket policy public-read và CORS.
* Loại bỏ AWS access key tĩnh khỏi CI bằng GitHub OIDC → IAM role.
* Áp dụng IAM Permission Boundaries để giới hạn quyền deploy role.
* Cấu hình `FightingGameServerInstanceRole` và quyền MatchMaker Lambda (DynamoDB, EC2 `DescribeInstances`).
* Xác minh pipeline deploy end-to-end: push GitHub → Actions → S3 client sync + CodeDeploy.
