---
title: "Xác minh SSH & kết quả"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.6.5.</b> "
---

## Bước 5 — Kiểm thử SSH

1. SSH từ máy cá nhân tới EC2 bằng key pair.

![Terminal SSH thành công](/images/5-Workshop/5.6-VPC-2Tier/10-ssh-success.png)

*Kết nối SSH thành công tới EC2 instance.*

## Kết quả mong đợi

- EC2 public kết nối được bằng SSH (và HTTP) từ internet
- Subnet Private không có đường ra internet