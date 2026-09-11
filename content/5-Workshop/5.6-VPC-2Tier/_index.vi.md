---
title: "VPC 2-tier"
date: 2026-09-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

## Mục tiêu

Thiết kế VPC 2 tầng: public subnet cho EC2 tiếp xúc internet và private subnet riêng dành cho tầng database — mô hình được tái sử dụng trong dự án Task Manager.

## Kiến trúc

![Sơ đồ kiến trúc VPC 2-tier](/images/5-Workshop/5.6-VPC-2Tier/01-diagram.png)

*Sơ đồ: Internet → IGW → Public Subnet (EC2); Private Subnet riêng biệt, cùng nằm trong 1 VPC.*

## Các mục con

1. [Tạo VPC & subnet](5.6.1-Create-VPC-and-Subnets/) — `10.0.0.0/16`, Public `10.0.1.0/24`, Private `10.0.2.0/24`.
2. [Internet Gateway & route table](5.6.2-IGW-and-Route-Table/) — `0.0.0.0/0` → IGW cho subnet Public.
3. [Tạo Security Group](5.6.3-Create-Security-Group/) — rule SSH và HTTP.
4. [Khởi chạy EC2](5.6.4-Launch-EC2/) — Amazon Linux 2023, t2.micro, subnet Public.
5. [Xác minh SSH & kết quả](5.6.5-Verify-SSH-and-Outcome/) — kết nối và xác nhận thiết kế.