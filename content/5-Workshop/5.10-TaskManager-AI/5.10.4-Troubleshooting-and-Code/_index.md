---
title: "Troubleshooting & code example"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.10.4.</b> "
---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Tasks always get `MEDIUM` priority even with an urgent description; the log shows `The AWS Access Key Id needs a subscription for the service` (HTTP 400) | Amazon Comprehend has not been **activated** for the account in the region in use. Open the AWS Console → switch to the correct region (`ap-southeast-1`) → find "Comprehend" → run **Real-time analysis** (Analyze) once to activate it — it is covered by the Free Tier. When the AI call fails, the system falls back to `MEDIUM` gracefully, so users see no crash |

## Code example

Excerpt from `AiAnalysisService` — calling Comprehend and mapping sentiment to priority:

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