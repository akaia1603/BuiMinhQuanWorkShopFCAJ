---
title: "Task Manager API — overview, tech stack & database"
date: 2026-09-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

## Problem statement

Task Manager API is a REST backend for small-scale work/project management: users register and sign in, create and manage **Projects**, and manage **Tasks** within each project with statuses `TODO`, `IN_PROGRESS`, `DONE`. Every time a task is created or updated, **Amazon Comprehend** analyzes it and suggests a priority level — this replaces the simple EC2 workshop originally planned and fulfils CLO3.

## Architecture

> **[Diagram — insert later]:** user → CloudFront + S3 (frontend) → EC2 Spring Boot API (public subnet) → RDS MySQL (private subnet); EC2 also calls Amazon Comprehend via an IAM Role — everything inside a single VPC.

## Components

- **Frontend:** plain HTML/CSS/JavaScript, hosted on **S3 + CloudFront**.
- **Backend:** REST API in Java Spring Boot on **EC2** (public subnet of the VPC).
- **Database:** MySQL on **Amazon RDS** (private subnet), reachable only from the EC2 Security Group.
- **AI service:** **Amazon Comprehend** called via an IAM Role attached to EC2 (no hardcoded Access Key) to detect sentiment and extract key phrases from task descriptions.

## Tech stack

| Component | Technology |
|-----------|------------|
| Language | Java 17 |
| Backend framework | Spring Boot 3.3, Spring Security, Spring Data JPA |
| Authentication | JWT (JSON Web Token), BCrypt password hashing |
| Database | MySQL 8.0 (Amazon RDS) |
| AI service | Amazon Comprehend (DetectSentiment, DetectKeyPhrases) |
| Frontend | HTML5, CSS3, plain JavaScript (Fetch API) |
| Packaging & deployment | Docker, Docker Compose |
| Cloud infra | Amazon EC2, Amazon RDS, Amazon VPC, IAM Role |
| Build tool | Apache Maven |
| API testing | Postman, curl |

## Database design

Three main tables: `users`, `projects`, `tasks`. `tasks` adds two columns for the AI feature: `priority` (`LOW`/`MEDIUM`/`HIGH`, suggested by the AI) and `ai_key_phrases` (key phrases extracted by Comprehend).

Relationships: one user owns many projects (**1–N**); one project contains many tasks (**1–N**); a task can be assigned to one user (`assignee`, **N–1**).

> **[Screenshot — insert later]:** ERD of the three tables (drawn with draw.io): users / projects / tasks.