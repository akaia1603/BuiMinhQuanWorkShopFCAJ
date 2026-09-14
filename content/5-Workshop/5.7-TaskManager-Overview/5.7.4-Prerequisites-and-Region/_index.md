---
title: "Prerequisites & Region"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.7.4.</b> "
aliases:
  - /5-workshop/5.1-workshop-overview/5.1.2-prerequisites-and-region/
---

## Prerequisites

- AWS account with admin access (or an IAM user able to manage S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch, IAM)
- Web browser (Chrome / Firefox / Edge)
- API testing tool: Postman or curl
- Local JDK 17, Maven, Docker (to build/test before deploying)

## Region

All services are deployed in **`ap-southeast-1`** (Singapore) — everything stays in a single region to avoid cross-region connection issues. Billing alarms must be created in **`us-east-1`** (see [5.3](../5.3-Cost-Monitoring)).