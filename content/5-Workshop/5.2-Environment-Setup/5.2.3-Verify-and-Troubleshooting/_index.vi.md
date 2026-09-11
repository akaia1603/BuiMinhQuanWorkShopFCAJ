---
title: "Xác minh & troubleshooting"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.2.3.</b> "
---

## Kết quả mong đợi

- Đồng hồ region hiển thị `ap-southeast-1` ở mọi thao tác Console
- Riêng Billing Alarm vẫn dùng `us-east-1` (alarm là region-specific, xem [5.3](../5.3-Cost-Monitoring))

![Console đã chọn ap-southeast-1](/images/5-Workshop/5.2-Environment-Setup/03-region-confirmed.png)

*Console sau khi đã chuyển đúng Region `ap-southeast-1` (góc trên bên phải hiển thị tên region đã chọn).*

## Troubleshooting

| Vấn đề | Kiểm tra |
|--------|----------|
| Tài nguyên tạo nhầm region khác | Xác nhận đồng hồ region góc trên bên phải trước mỗi thao tác |
| Gọi chéo dịch vụ bị lỗi | Các dịch vụ triển khai ở nhiều region — giữ tất cả tại `ap-southeast-1` |