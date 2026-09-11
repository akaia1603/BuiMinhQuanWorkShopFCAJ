---
title: "Giám sát chi phí — Budgets & CloudWatch"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## Mục tiêu

Thiết lập cơ chế giám sát trước khi triển khai bất kỳ dịch vụ nào phát sinh chi phí, đảm bảo không vượt ngưỡng Free Tier.

## Các mục con

1. [Tạo AWS Budget](5.3.1-Create-AWS-Budget/) — `FCAJ-Budget`, 5 USD/tháng với cảnh báo 50%/80%.
2. [Bật billing alerts](5.3.2-Enable-Billing-Alerts/) — `Receive Billing Alerts` tại `us-east-1`.
3. [Tạo CloudWatch billing alarm](5.3.3-Create-CloudWatch-Alarm/) — alarm trên `EstimatedCharges` > 5 USD.
4. [Xác minh & troubleshooting](5.3.4-Verify-and-Troubleshooting/) — kết quả mong đợi và lỗi thường gặp.