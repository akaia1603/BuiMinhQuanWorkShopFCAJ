---
title: "Task Manager — Amazon Comprehend AI"
date: 2026-09-01
weight: 10
chapter: false
pre: " <b> 5.10. </b> "
---

## Goal

Fulfil CLO3: integrate AI (Amazon Comprehend) into the backend. Instead of hardcoding an Access Key / Secret Key, permissions are granted through an **IAM Role attached to the EC2 instance** — the AWS best practice.

## Step 1 — Create the IAM role

1. **IAM → Roles → Create role**.
2. Trusted entity: **AWS service** → Use case: **EC2**.
3. In Permissions, find and tick the **`ComprehendReadOnly`** policy.
4. Name: `taskmanager-ec2-comprehend-role` → **Create role**.

## Step 2 — Attach the role to EC2

1. **EC2 Console → select the backend instance → Actions → Security → Modify IAM role**.
2. Choose the new role → **Update IAM role**.

## Step 3 — Restart & verify

1. Restart the backend service so the AWS SDK picks up the new permissions: `sudo systemctl restart taskmanager`.
2. Create a task with an urgent description (e.g. "Need to urgently fix a critical bug before the deadline").

## Expected outcome

- The task creation response includes `priority = HIGH` and `aiKeyPhrases` filled with the phrases Comprehend extracted
- No access keys in the code — permission comes from the instance role

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

> **[Screenshot — insert later]:** (1) IAM role page showing the attached ComprehendReadOnly policy; (2) EC2 instance details → "IAM role" showing the assigned role; (3) task creation response with `priority` and `aiKeyPhrases` filled automatically.