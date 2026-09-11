---
title: "Thiết kế cơ sở dữ liệu"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.7.3.</b> "
---

## Thiết kế cơ sở dữ liệu

Hệ thống sử dụng 3 bảng chính: `users`, `projects`, `tasks`. Bảng `tasks` có thêm 2 cột phục vụ tính năng AI: `priority` (`LOW`/`MEDIUM`/`HIGH`, do AI gợi ý) và `ai_key_phrases` (các từ khóa do Comprehend trích xuất).

Quan hệ: một user sở hữu nhiều project (**1–N**); một project chứa nhiều task (**1–N**); một task có thể được gán cho một user (`assignee`, quan hệ **N–1**).

![Sơ đồ ERD — users / projects / tasks](/images/5-Workshop/5.7-TaskManager-Overview/02-erd.png)

*Sơ đồ quan hệ thực thể (ERD) 3 bảng users / projects / tasks (vẽ bằng draw.io).*