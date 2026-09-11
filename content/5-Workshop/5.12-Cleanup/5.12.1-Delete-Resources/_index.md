---
title: "Delete the resources"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.12.1.</b> "
---

## Steps

- **RDS:** **Stop** or **Delete** `taskmanager-db` (note: Stop only pauses for a maximum of 7 days, then AWS restarts it automatically).

![Deleting the RDS instance](/images/5-Workshop/5.12-Cleanup/01-rds-delete.png)

*Deleting the `taskmanager-db` instance.*

- **EC2:** **Terminate** the instances used for the VPC workshop and the Task Manager API.

![Terminating the EC2 instances](/images/5-Workshop/5.12-Cleanup/02-ec2-terminate.png)

*Terminating the EC2 instances.*

- **CloudFront + S3:** **Disable** then **Delete** the distribution; empty and **Delete** the S3 bucket.

![Disabling the CloudFront distribution](/images/5-Workshop/5.12-Cleanup/03-cloudfront-delete.png)

*Disabling the CloudFront distribution.*

![Deleting the S3 bucket](/images/5-Workshop/5.12-Cleanup/04-s3-delete.png)

*Deleting the S3 bucket.*

- **Lambda + API Gateway + DynamoDB:** delete the Lambda function, the API Gateway, and the `fcaj-notes` DynamoDB table.

![Deleting Lambda and API Gateway](/images/5-Workshop/5.12-Cleanup/05-lambda-apigw-delete.png)

*Deleting the Lambda function and API Gateway.*

![Deleting the DynamoDB table](/images/5-Workshop/5.12-Cleanup/06-dynamodb-delete.png)

*Deleting the `fcaj-notes` DynamoDB table.*

- **IAM Role:** may be kept (no charge) or deleted if unused.
- Finally check the **Billing Dashboard** to confirm no resource is generating charges.