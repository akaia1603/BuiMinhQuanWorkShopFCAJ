---
title: "Troubleshooting & code minh họa"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.10.4.</b> "
---

## Troubleshooting

| Vấn đề | Giải pháp |
|--------|-----------|
| Task luôn được gợi ý `MEDIUM` dù mô tả khẩn cấp; log báo `The AWS Access Key Id needs a subscription for the service` (HTTP 400) | Dịch vụ Amazon Comprehend chưa được **kích hoạt** trong tài khoản ở region đang dùng. Vào AWS Console → chọn đúng region (`ap-southeast-1`) → tìm "Comprehend" → chạy thử **Real-time analysis** (Analyze) một lần để kích hoạt — nằm trong Free Tier. Khi AI lỗi, hệ thống chủ động fallback về `MEDIUM` nên người dùng không gặp sự cố |

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