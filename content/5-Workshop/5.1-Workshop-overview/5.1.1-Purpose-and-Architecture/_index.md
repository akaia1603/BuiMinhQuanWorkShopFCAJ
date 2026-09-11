---
title: "Purpose & architecture"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.1.1.</b> "
---

## Purpose

This workshop documents every AWS practice performed during the FCAJ internship in sequence: environment preparation, cost monitoring, foundational serverless and network workshops, then the main project — **Task Manager API**, a complete Java Spring Boot backend on **EC2 + RDS** that integrates **Amazon Comprehend** AI to suggest task priority automatically (fulfils CLO3).

Each page records the exact AWS Console steps and shows a screenshot at every point where evidence is required for the internship report.

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

![Overall architecture diagram](/images/5-Workshop/5.1-Workshop-overview/01-architecture.png)

*Diagram: user → CloudFront/S3 → EC2 Spring Boot → RDS MySQL; EC2 → Amazon Comprehend via IAM Role.*