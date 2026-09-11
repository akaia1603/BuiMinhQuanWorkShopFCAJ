---
title: "Problem statement & architecture"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.7.1.</b> "
---

## Problem statement

Task Manager API is a REST backend for small-scale work/project management: users register and sign in, create and manage **Projects**, and manage **Tasks** within each project with statuses `TODO`, `IN_PROGRESS`, `DONE`. Every time a task is created or updated, **Amazon Comprehend** analyzes it and suggests a priority level — this replaces the simple EC2 workshop originally planned and fulfils CLO3.

## Architecture

![Task Manager overall architecture](/images/5-Workshop/5.7-TaskManager-Overview/01-architecture.png)

*Diagram: user → Nginx on EC2 (frontend, port 80) → Spring Boot API (port 8080) → RDS MySQL (private subnet); EC2 also calls Amazon Comprehend via an IAM Role — everything inside a single VPC.*

> The frontend is served by Nginx running on the same EC2 as the backend; the **S3 + CloudFront** option is practiced separately in section [5.4](../5.4-S3-CloudFront).