---
title: "Trỏ frontend tới API"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.11.1.</b> "
---

## Bước 1 — Trỏ frontend tới API

1. Sửa biến `API_BASE` trong `frontend/js/config.js` thành địa chỉ EC2 thật: `http://<EC2-Public-IP>:8080`.

![Sửa API_BASE trong config.js](/images/5-Workshop/5.11-TaskManager-Frontend/01-config-js.png)

*`API_BASE` được đặt về địa chỉ public của EC2.*