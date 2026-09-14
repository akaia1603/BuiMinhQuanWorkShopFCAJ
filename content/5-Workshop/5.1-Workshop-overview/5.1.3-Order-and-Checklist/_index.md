---
title: "Workshop order, skills & checklist"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.1.3.</b> "
---

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