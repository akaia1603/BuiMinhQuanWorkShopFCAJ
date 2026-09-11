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

![Serverless notes API — architecture diagram](/images/5-Workshop/5.5-Serverless-API/01-diagram.png)

*Diagram: client → API Gateway → Lambda → DynamoDB.*

## Subsections

1. [Create the DynamoDB table](5.5.1-Create-DynamoDB-Table/) — `fcaj-notes`.
2. [Create the IAM role for Lambda](5.5.2-IAM-Role-for-Lambda/) — basic execution + DynamoDB access.
3. [Create the Lambda function](5.5.3-Create-Lambda-Function/) — Python 3.12, GET + POST handlers.
4. [Create the API Gateway](5.5.4-Create-API-Gateway/) — HTTP API with `GET /notes` and `POST /notes`.
5. [Test the API](5.5.5-Test-Notes-API/) — GET/POST in Postman.
6. [Expected outcome](5.5.6-Expected-Outcome/) — summary of the serverless result.