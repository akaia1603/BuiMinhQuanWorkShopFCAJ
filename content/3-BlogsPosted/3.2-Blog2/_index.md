---
title: "Blog 2"
date: 2026-09-13
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# REAL-TIME ANALYSIS OF CUSTOMER SENTIMENT USING AWS

Extracted from an AWS Machine Learning Blog case study: a near-real-time pipeline that analyzes customer review sentiment and extracts entity-level opinions using **Amazon Comprehend**, replacing a batch process that used to take 2–3 days with insights available within a few minutes.

### Key Architectural Components:

- **Ingestion & Buffering:** Customer reviews from the website or mobile app are sent through **Amazon API Gateway** into an **Amazon SQS** queue, which acts as a buffer and uses a dead-letter queue for failed messages.
- **Orchestration:** An **AWS Lambda** function triggers an **AWS Step Functions** state machine for each review, decoupling the analysis flow and adding reliability with retries.
- **Full & Targeted Sentiment:** The state machine calls **Amazon Comprehend** (`detect_sentiment`) for overall sentiment and `detect_targeted_sentiment` for entity-level opinions (e.g. company, product, brand), storing results in **Amazon DynamoDB**.
- **Alerting & Downstream Events:** When sentiment is negative or mixed, **Amazon SNS** notifies marketing/customer-service e-mails and **Amazon EventBridge** forwards the event to downstream systems.
- **Analytics & Dashboard:** **DynamoDB Streams → Amazon Kinesis Data Streams → Kinesis Data Firehose → Amazon S3**, then **Amazon QuickSight** visualizes the results in near-real time without SQL.

### Benefits of the Architecture:

- Delivers sentiment insights within a few minutes instead of days.
- Fully serverless — elastic scaling and no infrastructure to manage.
- No AI/ML or NLP expertise required: everything is handled by managed **Amazon Comprehend**.
- Ready-to-deploy as an **AWS CloudFormation** template behind any customer-facing application.

---

### Architecture Diagram:

![Real-time customer sentiment architecture](/images/3-BlogsPosted/blog2.png)

---

### Links and References:

- **Reference Article:** [Real-time analysis of customer sentiment using AWS](https://aws.amazon.com/blogs/machine-learning/real-time-analysis-of-customer-sentiment-using-aws/)