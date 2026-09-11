---
title: "Xác minh & troubleshooting"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.3.4.</b> "
---

## Kết quả mong đợi

- Dashboard Budget theo dõi chi phí trong tháng
- Nhận email cảnh báo tại 50% và 80% chi phí dự kiến cùng alarm khi vượt ngưỡng

## Troubleshooting

| Vấn đề | Kiểm tra |
|--------|----------|
| Billing metric không có dữ liệu | Bật **Receive Billing Alerts** tại `us-east-1` trước khi tạo alarm |
| Alarm không bao giờ kích hoạt | Ngưỡng so với tổng chi phí ước tính trong tháng; chờ metric đủ dữ liệu |