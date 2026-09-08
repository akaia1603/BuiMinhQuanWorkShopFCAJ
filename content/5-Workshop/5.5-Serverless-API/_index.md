---
title: "Serverless API — Lambda + API Gateway + DynamoDB"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

## Goal

Build a notes API entirely serverless: API Gateway → Lambda → DynamoDB, with no server to manage.

## Architecture

> **[Diagram — insert later]:** client → API Gateway → Lambda → DynamoDB.

## Step 1 — DynamoDB table

1. Create table `fcaj-notes`, Partition key: `id` (String), keep default settings (on-demand).

## Step 2 — IAM role for Lambda

1. Create an IAM Role for Lambda with two policies: `AWSLambdaBasicExecutionRole` and `AmazonDynamoDBFullAccess`.

## Step 3 — Lambda function

1. Create Lambda function `fcaj-notes-api`, runtime **Python 3.12**, attach the IAM role above.
2. Write code handling two methods — **GET** (list notes) and **POST** (add a note) — then **Deploy**.

## Step 4 — API Gateway

1. Create an **HTTP API** and integrate it with the Lambda function.
2. Add two routes: **GET /notes** and **POST /notes**.

## Step 5 — Test

1. Call **GET /notes** (expect an empty array on first run).
2. **POST /notes** with a sample payload, then call **GET /notes** again to confirm the item was persisted in DynamoDB.

## Expected outcome

- GET/POST respond with JSON and DynamoDB stores the note
- No servers to manage — everything is serverless

> **[Screenshot — insert later]:** (1) DynamoDB table with the new item; (2) Lambda function source code; (3) API Gateway route list; (4) successful GET/POST responses in Postman (JSON response).