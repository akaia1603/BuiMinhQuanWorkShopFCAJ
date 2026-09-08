---
title: "Task Manager — tích hợp AI Amazon Comprehend"
date: 2026-09-01
weight: 10
chapter: false
pre: " <b> 5.10. </b> "
---

## Mục tiêu

Đáp ứng CLO3: tích hợp AI (Amazon Comprehend) vào backend. Thay vì hardcode Access Key / Secret Key — vốn không an toàn — hệ thống được cấp quyền gọi Comprehend thông qua **IAM Role gắn trực tiếp vào EC2 instance**, theo đúng thực hành chuẩn của AWS.

## Bước 1 — Tạo IAM Role

1. **IAM → Roles → Create role**.
2. Trusted entity: **AWS service** → Use case: **EC2**.
3. Ở bước Permissions, tìm và tick policy **`ComprehendReadOnly`**.
4. Đặt tên role: `taskmanager-ec2-comprehend-role` → **Create role**.

## Bước 2 — Gắn role vào EC2

1. **EC2 Console → chọn instance đang chạy backend → Actions → Security → Modify IAM role**.
2. Chọn role vừa tạo → **Update IAM role**.

## Bước 3 — Khởi động lại & kiểm thử

1. Khởi động lại service backend để AWS SDK nhận quyền mới: `sudo systemctl restart taskmanager`.
2. Tạo task với mô tả có sắc thái khẩn cấp (vd: "Cần sửa gấp lỗi nghiêm trọng trước hạn nộp").

## Kết quả mong đợi

- Response tạo task trả về `priority = HIGH` và `aiKeyPhrases` chứa các cụm từ khóa do Comprehend trích xuất
- Không có bất kỳ access key nào trong code — quyền lấy từ instance role

## Code minh họa

Trích từ lớp `AiAnalysisService` — gọi Amazon Comprehend và ánh xạ sentiment sang mức độ ưu tiên:

```java
public AiInsight analyze(String text) {
    DetectSentimentRequest sentimentReq = DetectSentimentRequest.builder()
            .text(text)
            .languageCode(LanguageCode.VI)
            .build();
    DetectSentimentResponse sentimentRes = getClient().detectSentiment(sentimentReq);
    SentimentType sentiment = sentimentRes.sentiment();

    Task.Priority priority = mapSentimentToPriority(sentiment);
    return new AiInsight(priority, extractedKeyPhrases);
}
```

> **[CHỤP MÀN HÌNH — chưa chèn ảnh]:** (1) trang IAM Role hiển thị policy ComprehendReadOnly đã gắn; (2) mục "IAM role" trong EC2 instance details hiển thị đúng role vừa gán; (3) response JSON của API tạo task có trường `priority` và `aiKeyPhrases` được điền tự động.