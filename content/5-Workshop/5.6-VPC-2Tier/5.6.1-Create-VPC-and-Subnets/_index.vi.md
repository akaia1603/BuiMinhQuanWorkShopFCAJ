---
title: "Tạo VPC & subnet"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.6.1.</b> "
---

## Bước 1 — VPC & subnet

1. Tạo VPC với CIDR `10.0.0.0/16`.

![Tạo VPC](/images/5-Workshop/5.6-VPC-2Tier/02-create-vpc.png)

*Đang tạo VPC với CIDR `10.0.0.0/16`.*

2. Tạo 2 subnet: Public `10.0.1.0/24` và Private `10.0.2.0/24`, đặt ở 2 Availability Zone khác nhau.

![Tạo các subnet](/images/5-Workshop/5.6-VPC-2Tier/03-create-subnets.png)

*Hai subnet — public và private.*