---
title: "Giám sát chi phí — Budgets & CloudWatch"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## Mục tiêu

Thiết lập cơ chế giám sát trước khi triển khai bất kỳ dịch vụ nào phát sinh chi phí, đảm bảo không vượt ngưỡng Free Tier.

## Bước 1 — Tạo AWS Budget

1. Tại thanh tìm kiếm gõ `Budgets` → **AWS Budgets → Create budget**.
2. Chọn **Customize (advanced)** → **Cost budget**.
3. Đặt tên `FCAJ-Budget`, Period: **Monthly**, Budgeted amount: **5 USD**.
4. Thêm 2 ngưỡng cảnh báo tại **50%** và **80%**, nhập email nhận thông báo → **Create budget**.

## Bước 2 — Bật billing alerts

1. Chuyển Region sang **`us-east-1` (N. Virginia)**.
2. Vào **Billing Preferences**, bật **Receive Billing Alerts**.

## Bước 3 — Tạo CloudWatch billing alarm

1. **CloudWatch → Alarms → Billing → Create alarm**.
2. Chọn metric **`EstimatedCharges`**, ngưỡng **> 5 USD**.
3. Tạo SNS topic gửi email cảnh báo → **Create alarm**.

## Kết quả mong đợi

- Dashboard Budget theo dõi chi phí trong tháng
- Nhận email cảnh báo tại 50% và 80% chi phí dự kiến cùng alarm khi vượt ngưỡng

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) trang danh sách Budget hiển thị `FCAJ-Budget`; (2) trang CloudWatch Alarms hiển thị alarm ở trạng thái `OK`; (3) email xác nhận subscription từ AWS Notifications.

## Troubleshooting

| Vấn đề | Kiểm tra |
|--------|----------|
| Billing metric không có dữ liệu | Bật **Receive Billing Alerts** tại `us-east-1` trước khi tạo alarm |
| Alarm không bao giờ kích hoạt | Ngưỡng so với tổng chi phí ước tính trong tháng; chờ metric đủ dữ liệu |