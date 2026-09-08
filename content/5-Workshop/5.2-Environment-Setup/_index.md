---
title: "Environment setup & Region"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

## Goal

Prepare the AWS account and agree on a single Region before deploying any service, to avoid cross-region connection errors.

## Prerequisites

- AWS root account or IAM user able to manage S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch and IAM
- Web browser (Chrome / Firefox / Edge)
- Postman or curl for API testing
- JDK 17, Maven and Docker installed locally (to build/test before deploying)

## Step 1 — Sign in to the console

1. Open https://console.aws.amazon.com and sign in.

## Step 2 — Select the Region

1. In the top-right corner of the navigation bar, choose **Asia Pacific (Singapore) — `ap-southeast-1`** (or the region agreed with the FCAJ program).
2. All services in this report are deployed in this same region.

## Expected outcome

- Region selector shows `ap-southeast-1` for every console action
- Billing alarms still use `us-east-1` (they are region-specific, see [5.3](5.3-Cost-Monitoring/))

> **[Screenshot — insert later]:** Console with the correct Region `ap-southeast-1` shown in the top-right corner.

## Troubleshooting

| Issue | Check |
|-------|-------|
| Resources created in a different region | Confirm the region selector top-right before every console action |
| Cross-service calls fail | Services deployed in different regions — keep everything in `ap-southeast-1` |