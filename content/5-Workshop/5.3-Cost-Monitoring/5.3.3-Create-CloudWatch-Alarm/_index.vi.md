---
title: "Tạo CloudWatch billing alarm"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.3.3.</b> "
---

## Bước 3 — Tạo CloudWatch billing alarm

1. **CloudWatch → Alarms → Billing → Create alarm**.
2. Chọn metric **`EstimatedCharges`**, ngưỡng **> 5 USD**.
3. Tạo SNS topic gửi email cảnh báo → **Create alarm**.

![Tạo CloudWatch billing alarm](/images/5-Workshop/5.3-Cost-Monitoring/05-cloudwatch-alarm-create.png)

*Đang tạo billing alarm trên metric `EstimatedCharges`.*

![Billing alarm ở trạng thái OK](/images/5-Workshop/5.3-Cost-Monitoring/06-cloudwatch-alarm-ok.png)

*Alarm hiển thị ở trạng thái `OK`.*

![Email xác nhận subscription AWS Notifications](/images/5-Workshop/5.3-Cost-Monitoring/07-subscription-email.png)

*Email xác nhận subscription từ AWS Notifications.*