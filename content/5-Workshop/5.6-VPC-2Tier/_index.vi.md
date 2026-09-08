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

> **[Sơ đồ — chưa chèn ảnh]:** Internet → IGW → Public Subnet (EC2); Private Subnet riêng biệt, cùng nằm trong 1 VPC.

## Bước 1 — VPC & subnet

1. Tạo VPC với CIDR `10.0.0.0/16`.
2. Tạo 2 subnet: Public `10.0.1.0/24` và Private `10.0.2.0/24`, đặt ở 2 Availability Zone khác nhau.

## Bước 2 — Internet Gateway & route table

1. Tạo **Internet Gateway**, gắn vào VPC.
2. Tạo route table cho subnet Public, thêm route `0.0.0.0/0` → Internet Gateway, gán vào subnet Public.
3. Subnet Private giữ route table mặc định (không có đường ra internet).

## Bước 3 — Security Group

1. Tạo Security Group cho phép **SSH (port 22, nguồn: My IP)** và **HTTP (port 80, nguồn: Anywhere)**.

## Bước 4 — Khởi chạy EC2

1. Khởi chạy **EC2 instance (Amazon Linux 2023, t2.micro)** trong subnet Public.
2. Bật **Auto-assign public IP**, gắn Security Group vừa tạo.

## Bước 5 — Kiểm thử SSH

1. SSH từ máy cá nhân tới EC2 bằng key pair.

## Kết quả mong đợi

- EC2 public kết nối được bằng SSH (và HTTP) từ internet
- Subnet Private không có đường ra internet

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) sơ đồ Resource map của VPC; (2) cấu hình Route Table; (3) cấu hình Security Group; (4) terminal kết nối SSH thành công tới EC2.