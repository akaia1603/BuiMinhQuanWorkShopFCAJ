---
title: "Workshop overview"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

## Purpose

This section documents every AWS practice performed during the FCAJ internship in sequence: environment preparation, cost monitoring, foundational serverless and network workshops, then the main project — **Task Manager API**, a complete Java Spring Boot backend on **EC2 + RDS** that integrates **Amazon Comprehend** AI to suggest task priority automatically (fulfils CLO3).

Each page records the exact AWS Console steps and marks `[Screenshot]` at every point where a screenshot is required as evidence for the internship report.

## Architecture (main project)

| Component | Technology / Service |
|-----------|----------------------|
| Frontend | Static HTML/CSS/JS on S3 + CloudFront |
| Backend | Java 17, Spring Boot 3.3 (Spring Security, Spring Data JPA) on EC2 |
| Database | MySQL 8.0 on Amazon RDS (private subnet) |
| AI | Amazon Comprehend — DetectSentiment, DetectKeyPhrases |
| Auth | JWT, BCrypt password encoding |
| Packaging | Maven, Docker, Docker Compose |
| Infra | EC2, RDS, VPC, S3, CloudFront, IAM Role |

> **[Screenshot — insert later]:** overall architecture diagram (user → CloudFront/S3 → EC2 Spring Boot → RDS MySQL; EC2 → Amazon Comprehend via IAM Role).

## Prerequisites

- AWS account with admin access (or an IAM user able to manage S3, CloudFront, Lambda, API Gateway, DynamoDB, VPC, EC2, RDS, Comprehend, Budgets, CloudWatch, IAM)
- Web browser (Chrome / Firefox / Edge)
- API testing tool: Postman or curl
- Local JDK 17, Maven, Docker (to build/test before deploying)

## Region

All services are deployed in **`ap-southeast-1`** (Singapore) — everything stays in a single region to avoid cross-region connection issues. Billing alarms must be created in **`us-east-1`** (see [5.3](5.3-Cost-Monitoring/)).

## Workshop order

Complete **5.2 → 5.11** in sequence; later pages depend on the VPC, EC2 and RDS resources from earlier pages. **5.12** documents the teardown.

## Skills & tools

- RESTful API design and implementation
- JWT authentication + Spring Security
- Relational database design + ORM (Spring Data JPA / Hibernate)
- AWS deployment (EC2, RDS) with safe networking (VPC, Security Groups, private subnet for the database)
- AI integration via IAM Role (no hardcoded credentials)
- Docker / Docker Compose packaging
- Cost monitoring (Budgets, CloudWatch)
- API testing with Postman / curl

## Verification checklist

- [ ] Budget `FCAJ-Budget` and Billing Alarm active (alerts at 50% / 80%)
- [ ] Static site reachable via the CloudFront URL with HTTPS
- [ ] Serverless API GET/POST `/notes` works against DynamoDB
- [ ] VPC 2-tier with public/private subnets and SSH access to EC2
- [ ] RDS private; EC2 connects to MySQL on port 3306 via Security Group
- [ ] Task creation returns `priority` + `aiKeyPhrases` from Amazon Comprehend
- [ ] All resources cleaned up after the report is delivered