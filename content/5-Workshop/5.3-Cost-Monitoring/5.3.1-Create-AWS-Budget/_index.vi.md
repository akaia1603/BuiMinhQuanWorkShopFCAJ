---
title: "Tạo AWS Budget"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.3.1.</b> "
---

## Bước 1 — Tạo AWS Budget

1. Tại thanh tìm kiếm gõ `Budgets` → **AWS Budgets → Create budget**.
2. Chọn **Customize (advanced)** → **Cost budget**.

![Mở AWS Budgets](/images/5-Workshop/5.3-Cost-Monitoring/01-budget-menu.png)

*Trang AWS Budgets nơi tạo budget.*

3. Đặt tên `FCAJ-Budget`, Period: **Monthly**, Budgeted amount: **5 USD**.

![Cấu hình tạo budget với tên và số tiền](/images/5-Workshop/5.3-Cost-Monitoring/02-budget-create.png)

*Cấu hình budget: `FCAJ-Budget`, Monthly, 5 USD.*

4. Thêm 2 ngưỡng cảnh báo tại **50%** và **80%**, nhập email nhận thông báo → **Create budget**.

![Danh sách Budget hiển thị FCAJ-Budget](/images/5-Workshop/5.3-Cost-Monitoring/03-budget-list.png)

*Trang danh sách Budget hiển thị `FCAJ-Budget`.*