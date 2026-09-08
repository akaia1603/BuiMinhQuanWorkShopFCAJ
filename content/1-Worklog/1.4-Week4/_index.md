---
title: "Week 4 Worklog"
date: 2026-08-15
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Set up cost monitoring with AWS Budgets and CloudWatch billing alarms.
* Complete the static website workshop (S3 + CloudFront) and the serverless notes API workshop (Lambda + API Gateway + DynamoDB).

**Period:** 15/08/2026 – 21/08/2026

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Create budget `FCAJ-Budget` (Monthly, $5) with alerts at 50% and 80% <br> - Enable Receive Billing Alerts (us-east-1) and create a CloudWatch billing alarm (> $5) | 17/08/2026 | 17/08/2026 | AWS Billing docs |
| 3 | - Create an S3 bucket, upload `index.html`, enable static website hosting, add a public-read bucket policy | 18/08/2026 | 18/08/2026 | AWS S3 docs |
| 4 | - Create a CloudFront distribution (HTTPS) pointing to the bucket and verify the site loads | 19/08/2026 | 19/08/2026 | AWS CloudFront docs |
| 5 | - Create DynamoDB table `fcaj-notes` and the IAM role for Lambda <br> - Write the `fcaj-notes-api` Lambda (Python 3.12) handling GET/POST | 20/08/2026 | 20/08/2026 | AWS Lambda docs |
| 6 | - Create the HTTP API on API Gateway with routes `GET /notes` and `POST /notes` <br> - **Test:** call GET/POST via Postman and confirm items persist in DynamoDB | 21/08/2026 | 21/08/2026 | |

### Week 4 Achievements:

* Configured AWS Budgets and a CloudWatch billing alarm before deploying any paid service — all within the Free Tier.
* Hosted a static website on S3 and served it over HTTPS through CloudFront.
* Built and tested a fully serverless notes API: API Gateway → Lambda → DynamoDB.
* Gained hands-on experience with IAM roles for Lambda and HTTP API routing.
* Consolidated the AWS CLI/DynamoDB skills from earlier weeks into a working end-to-end serverless flow.