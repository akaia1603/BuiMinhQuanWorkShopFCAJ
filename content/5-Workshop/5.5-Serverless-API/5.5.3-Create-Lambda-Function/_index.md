---
title: "Create the Lambda function"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.5.3.</b> "
---

## Step 3 — Lambda function

1. Create Lambda function `fcaj-notes-api`, runtime **Python 3.12**, attach the IAM role above.

![Creating the Lambda function](/images/5-Workshop/5.5-Serverless-API/05-lambda-create.png)

*The Lambda function creation page.*

2. Write code handling two methods — **GET** (list notes) and **POST** (add a note) — then **Deploy**.

![Lambda source code](/images/5-Workshop/5.5-Serverless-API/06-lambda-code.png)

*The Lambda function source code.*