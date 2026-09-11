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

## Subsections

1. [Sign in to the console](5.2.1-Sign-in-to-Console/) — login to AWS.
2. [Select the Region](5.2.2-Select-Region/) — choose `ap-southeast-1`.
3. [Verify & troubleshooting](5.2.3-Verify-and-Troubleshooting/) — expected outcome and common issues.