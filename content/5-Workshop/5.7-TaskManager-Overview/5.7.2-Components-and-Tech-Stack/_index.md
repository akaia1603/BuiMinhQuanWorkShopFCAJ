---
title: "Components & tech stack"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.7.2.</b> "
---

## Components

- **Frontend:** plain HTML/CSS/JavaScript, served by **Nginx** running on the EC2 instance itself; the S3 + CloudFront option is practiced separately in section [5.4](../5.4-S3-CloudFront).
- **Backend:** REST API in Java Spring Boot on **EC2** (public subnet of the VPC).
- **Database:** MySQL on **Amazon RDS** (private subnet), reachable only from the EC2 Security Group.
- **AI service:** **Amazon Comprehend** called via an IAM Role attached to EC2 (no hardcoded Access Key) to detect sentiment and extract key phrases from task descriptions.

## Tech stack

| Component | Technology |
|-----------|------------|
| Language | Java 17 |
| Backend framework | Spring Boot 3.3, Spring Security, Spring Data JPA |
| Authentication | JWT (JSON Web Token), BCrypt password hashing |
| Database | MySQL 8.x (Amazon RDS) |
| AI service | Amazon Comprehend (DetectSentiment, DetectKeyPhrases) |
| Frontend | HTML5, CSS3, plain JavaScript (Fetch API), Nginx (web server) |
| Packaging & deployment | Docker, Docker Compose |
| Cloud infra | Amazon EC2, Amazon RDS, Amazon VPC, IAM Role |
| Build tool | Apache Maven |
| API testing | Postman, curl |