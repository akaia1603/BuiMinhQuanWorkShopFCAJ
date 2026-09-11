---
title: "Test the notes API"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.5.5.</b> "
---

## Step 5 — Test

1. Call **GET /notes** (expect an empty array on first run).

![DynamoDB item persisted](/images/5-Workshop/5.5-Serverless-API/09-dynamodb-item.png)

*The DynamoDB table with the new item.*

2. **POST /notes** with a sample payload, then call **GET /notes** again to confirm the item was persisted in DynamoDB.

![GET /notes response in Postman](/images/5-Workshop/5.5-Serverless-API/10-postman-get.png)

*Successful GET response in Postman.*

![POST /notes response in Postman](/images/5-Workshop/5.5-Serverless-API/11-postman-post.png)

*Successful POST response in Postman.*