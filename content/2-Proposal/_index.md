---
title: "Proposal"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Task Manager API — Full-Stack Backend with AI on AWS

## A Complete Java Spring Boot Application on EC2 + RDS with Amazon Comprehend

---

### 1. Executive Summary

This project proposal describes the main hands-on work of the internship: build and deploy a complete REST backend called **Task Manager API** on AWS. The system lets users register and sign in, manage projects and tasks, and relies on **Amazon Comprehend** (AI) to automatically analyze every task description and suggest a priority level.

The internship also covers a set of stage-setting AWS workshops in the same Region (`ap-southeast-1`): cost monitoring (Budgets + CloudWatch), static website hosting (S3 + CloudFront), a serverless notes API (Lambda + API Gateway + DynamoDB) and a 2-tier VPC design. These workshops build up the skills needed for the main project.

---

### 2. Problem Statement

#### What's the Problem?

Small teams usually manage work in spreadsheets or heavyweight tools that are hard to customize. There was no simple, self-built backend that (1) manages projects and tasks with proper authentication, and (2) demonstrates how an AI service can be embedded into a normal application without hardcoding credentials.

#### The Solution

A full-stack system deployed on AWS:

- **Frontend:** plain HTML/CSS/JS hosted on S3 + CloudFront (HTTPS).
- **Backend:** Java 17 + Spring Boot 3.3 (Spring Security JWT, Spring Data JPA) on an EC2 instance.
- **Database:** MySQL 8.0 on Amazon RDS inside a private subnet.
- **AI:** Amazon Comprehend (DetectSentiment, DetectKeyPhrases) called through an IAM Role attached to the EC2 instance — no hardcoded Access Keys (fulfils CLO3).
- **Networking:** 2-tier VPC (public subnet for EC2, private subnet for RDS).

#### Benefits

- **Realistic full-stack deployment:** every layer of a modern application is deployed on AWS securely.
- **Safe AI integration:** least-privilege IAM role instead of static keys.
- **Cost control:** AWS Budgets + CloudWatch billing alarm keep everything within the Free Tier.
- **Reproducible:** Maven + Docker packaging, configured via environment variables (`app.env`).

---

### 3. Solution Architecture

The architecture follows a standard 3-tier model inside a single VPC:

- **Client tier:** static frontend on S3, served through CloudFront over HTTPS.
- **Application tier:** EC2 instance (public subnet) running the Spring Boot REST API on port 8080.
- **Data tier:** RDS MySQL (private subnet), reachable only from the EC2 Security Group on port 3306.
- **AI service:** Amazon Comprehend called by EC2 via its instance IAM Role.

The serverless workshops reuse the same networking concepts: the notes API uses API Gateway + Lambda + DynamoDB, and the static site uses S3 + CloudFront, sharing the Region and cost-monitoring setup.

#### AWS Services Used

- **Amazon S3 + CloudFront:** static frontend hosting over HTTPS
- **AWS Lambda + API Gateway + DynamoDB:** serverless notes API workshop
- **Amazon VPC, EC2, RDS:** 2-tier network and the main project runtime
- **IAM:** roles/policies including the EC2 instance role for Comprehend read-only access
- **Amazon Comprehend:** sentiment and key-phrase analysis for task priority
- **AWS Budgets + CloudWatch:** cost monitoring and billing alarms

---

### 4. Technical Implementation

#### Implementation Phases

1. **Phase 1: Environment & cost control (Week 1–3)**  
   AWS account setup, Region selection (`ap-southeast-1`), AWS Budgets + CloudWatch billing alarm.
2. **Phase 2: Foundational workshops (Week 4)**  
   Static website (S3 + CloudFront), serverless notes API (Lambda + API Gateway + DynamoDB).
3. **Phase 3: VPC 2-tier & main project (Week 5)**  
   VPC/Subnets/IAM, RDS MySQL, Spring Boot backend on EC2.
4. **Phase 4: AI integration & delivery (Week 6–7)**  
   Comprehend via IAM Role, frontend + end-to-end testing, cleanup, report.

#### Technical Requirements

- **Backend:** Java 17, Spring Boot 3.3, Spring Security (JWT), Spring Data JPA
- **Build:** Maven (`mvn clean package -DskipTests`), Docker for packaging
- **Infrastructure:** EC2 (Amazon Linux 2023, t2.micro), RDS MySQL `db.t3.micro`, VPC 2-tier, SG least-privilege
- **AI:** AWS SDK for Java calling DetectSentiment / DetectKeyPhrases
- **Security:** JWT + BCrypt, database private, permissions via IAM Role (no static keys)

---

### 5. Timeline & Milestones

- **Week 1–3:** AWS basics, account security, storage/CLI practice, cost monitoring.
- **Week 4:** S3 + CloudFront hosting and the serverless notes API workshops.
- **Week 5:** VPC 2-tier, RDS, and Spring Boot backend deployed on EC2.
- **Week 6:** Comprehend AI integration, frontend, end-to-end testing.
- **Week 7:** Resource cleanup and final report delivery.

---

### 6. Budget Estimation & Cost Optimization

- **Free Tier focus:** `t2.micro` / `db.t3.micro` and on-demand serverless stay within AWS Free Tier limits.
- **Proactive monitoring:** AWS Budgets (`FCAJ-Budget`, $5/month) with 50%/80% alerts plus a CloudWatch billing alarm.
- **Cleanup discipline:** documented teardown immediately after the report is delivered.

---

### 7. Risk Assessment

| Risk Item | Impact | Probability | Mitigation Strategy |
| --- | --- | --- | --- |
| RDS not reachable from EC2 | High | Medium | Connect only via RDS Security Group inbound 3306 with EC2 SG as source |
| Billing overrun | Medium | Low | Budget alerts + billing alarm configured before any paid service |
| AI requests fail / permissions missing | Medium | Low | IAM Role with `ComprehendReadOnly` attached to the instance; restart service after role change |
| Credentials leak | High | Low | No hardcoded Access Keys anywhere; all config via `app.env` / environment variables |

---

### 8. Expected Outcomes

- A working Task Manager REST API with JWT auth, CRUD for projects/tasks, and status assignment.
- AI-suggested task priority and key-phrase extraction via Amazon Comprehend.
- Secure deployment on AWS (private DB, least-privilege IAM, HTTPS frontend).
- Documented, reusable workshop guides and a cleaned-up AWS account at the end.