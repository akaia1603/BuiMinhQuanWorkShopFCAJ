---
title: "Sự kiện 1"
date: 2026-07-25
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# AWS Vietnam Community Meetup — Bài thu hoạch

**Sự kiện:** AWS Vietnam Community Meetup — Xu hướng AI & Kiến trúc Agentic trên AWS  
**Thời gian:** Thứ Bảy, 25/07/2026 – 08:30 đến 12:00 (check-in 08:30, chương trình bắt đầu lúc 09:00)  
**Địa điểm:** AWS Hà Nội – Tầng 7, Grand Terra Tower, 36 Cát Linh, Đống Đa, Hà Nội  
**Vai trò:** Người tham dự

## Tổng quan sự kiện

Buổi meetup cộng đồng AWS nửa ngày quy tụ các AWS Community Hero, Community Builder và kỹ sư đang trực tiếp triển khai AI trong doanh nghiệp. Chương trình bao gồm các xu hướng AI mới nhất và cách ứng dụng trên AWS, từ AI agent mã nguồn mở đến lựa chọn mẫu agent phù hợp; kèm tea break & networking cùng quiz Kahoot và lucky draw với quà tặng từ cộng đồng AWS.

## Chương trình & diễn giả

| # | Phiên | Diễn giả |
|---|---------|---------|
| 1 | **Community Update** — cập nhật hoạt động mới nhất của cộng đồng AWS Việt Nam | **Hồ Việt Anh** & **Phong Phạm** |
| 2 | **OpenClaw — The Rise and Practice of Open-Source AI Agents** | **Tuấn Vũ** |
| 3 | **From AI Trends to Business Value** | **Nguyễn Thu** & **Nam La** |
| 4 | **Ship Fast with AI, Not by** | **Henry (Đức) Bùi** |
| 5 | **Selecting the Right AI Agent Pattern on AWS** | **Dũng Lương** |

---

## Tóm tắt nội dung

### Community Update — Hồ Việt Anh & Phong Phạm

Phiên khai mạc tổng hợp các hoạt động mới nhất của cộng đồng AWS Việt Nam: nhóm học tập, meetup và chương trình First Cloud AI Journey. BTC khuyến khích mọi người đóng góp lại cho cộng đồng — viết blog, chia sẻ kinh nghiệm và hỗ trợ các bạn khóa sau — để kiến thức liên tục lan tỏa sau mỗi kỳ thực tập.

---

### Tuấn Vũ — OpenClaw: Sự trỗi dậy và thực hành AI agent mã nguồn mở

Tuấn Vũ giới thiệu **OpenClaw**, một framework AI agent mã nguồn mở mới nổi, và so sánh với các agent đóng gói do nhà cung cấp quản lý. Anh trình bày cách thiết lập, tích hợp tool và demo trực tiếp một agent có thể lập kế hoạch và thực thi các tác vụ nhiều bước.

**Điểm chính:**
- Agent mã nguồn mở cho team **minh bạch và toàn quyền kiểm soát** prompt, tool và cách triển khai — quan trọng với chi phí và tuân thủ trong doanh nghiệp.
- Agent chỉ mạnh bằng **hệ sinh thái tool** của nó (tìm kiếm web, thực thi mã, truy cập file/DB), nên thiết kế tầng tool đáng tin cậy quan trọng hơn mô hình nền.
- Framework cộng đồng cải tiến nhanh nhưng cần **đánh giá bảo mật và bảo trì** trước khi đưa vào production.

---

### Nguyễn Thu & Nam La — Từ xu hướng AI đến giá trị kinh doanh

Phiên này chuyển từ sự hào nhoáng của các xu hướng AI sang **giá trị kinh doanh**. Diễn giả cho rằng câu hỏi thắng cuộc không phải "AI làm được gì?" mà là "kết quả kinh doanh nào được mở ra và có đo được không?"

**Điểm chính:**
- Đặt các sáng kiến AI trong khuôn khổ **kết quả đo lường được** (tiết kiệm chi phí, giảm thời gian, tăng doanh thu) thay vì khả năng của mô hình.
- Bắt đầu từ một **nỗi đau thực tế, xảy ra thường xuyên** của doanh nghiệp, rồi chọn công cụ đơn giản nhất giải quyết được.
- **Sẵn sàng dữ liệu và quản trị thay đổi** là hai rào cản phi kỹ thuật lớn nhất khi ứng dụng AI.

---

### Henry (Đức) Bùi — Ship fast with AI, not by (AI)

Henry dùng AI để **tăng tốc bàn giao** nhưng vẫn giữ phán đoán kỹ thuật của con người — "ship nhanh với AI, không phải giao phó mù quáng cho AI". Anh khuyến nghị dùng AI cho việc scaffold, hỗ trợ review code và các refactor tẻ nhạt, còn kỹ sư chịu trách nhiệm về kiến trúc, chất lượng và bảo mật.

**Điểm chính:**
- Dùng AI làm **tăng tốc cho phần nhàm chán**, dành sự tập trung của con người cho thiết kế và tính đúng đắn.
- Giữ **human-in-the-loop** cho mọi thứ chạm tới production hoặc dữ liệu nhạy cảm; không bao giờ merge output AI chưa kiểm chứng lên production.
- Ship nhanh vẫn cần **kỷ luật**: test, review và đường rollback.

---

### Dũng Lương — Lựa chọn mẫu AI agent phù hợp trên AWS

Dũng Lương trình bày một khung quyết định để chọn **mẫu agent phù hợp trên AWS**, đối chiếu mức độ phức tạp với bài toán thay vì lúc nào cũng dùng nền tảng agentic cồng kềnh.

**Điểm chính:**
- Hiểu quang phổ từ **gọi prompt + tool đơn giản** đến **hệ multi-agent có điều phối**, và chọn mẫu nhẹ nhất giải quyết được bài toán.
- Trên AWS, cân nhắc agent **Amazon Bedrock**, hệ sinh thái **MCP** và orchestration theo hướng **Lambda-first** để kiểm soát chi phí và quan sát hệ thống.
- Thiết kế vì **quan sát được, guardrail và khả năng kiểm toán** — rất quan trọng khi agent được cấp quyền truy cập tool.

---

## Bài học thu được

- Giá trị của một agent nằm ở **tầng tool và ngữ cảnh**, không chỉ ở mô hình bên dưới.
- Luôn gắn AI với **kết quả kinh doanh đo lường được**, không phải danh sách tính năng.
- **Human-in-the-loop** là yêu cầu bắt buộc với mọi thứ chạm tới production hoặc dữ liệu nhạy cảm.
- Chọn **mẫu agent đơn giản nhất** giải quyết được vấn đề, rồi mới tiến hóa thêm.
- Cộng đồng AWS Việt Nam là nơi cởi mở, đề cao sự đóng góp, đáng để gắn bó lâu dài sau kỳ thực tập.

## Suy ngẫm cá nhân

Đây là sự kiện đầu tiên em tham dự đúng thời điểm bắt đầu thực tập, giúp em có cái nhìn tổng quan về cách AWS kết nối với hệ sinh thái Việt Nam. Thông điệp xuyên suốt — xây sản phẩm thật, hiểu những gì mình ship và gắn công việc AI với giá trị kinh doanh — đã định hướng rõ tư duy cloud engineering em muốn phát triển trong chương trình. Sự kiện cũng giới thiệu em đến với cộng đồng các nhà xây dựng và người hướng dẫn mà em có thể học hỏi suốt kỳ thực tập.