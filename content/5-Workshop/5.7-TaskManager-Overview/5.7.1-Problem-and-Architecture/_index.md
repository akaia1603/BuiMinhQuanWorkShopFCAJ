---
title: "Problem statement & architecture"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.7.1.</b> "
aliases:
  - /5-workshop/5.1-workshop-overview/5.1.1-purpose-and-architecture/
---

## Purpose

This workshop documents every AWS practice performed during the FCAJ internship in sequence: environment preparation, cost monitoring, foundational serverless and network workshops, then the main project — **Task Manager API**, a complete Java Spring Boot backend on **EC2 + RDS** that integrates **Amazon Comprehend** AI to suggest task priority automatically (fulfils CLO3).

Each page records the exact AWS Console steps and shows a screenshot at every point where evidence is required for the internship report.

## Problem statement

Task Manager API is a REST backend for small-scale work/project management: users register and sign in, create and manage **Projects**, and manage **Tasks** within each project with statuses `TODO`, `IN_PROGRESS`, `DONE`. Every time a task is created or updated, **Amazon Comprehend** analyzes it and suggests a priority level — this replaces the simple EC2 workshop originally planned and fulfils CLO3.

## Architecture

![Task Manager overall architecture](/images/5-Workshop/5.7-TaskManager-Overview/01-architecture.jpg)

*Diagram: user → Nginx on EC2 (frontend, port 80) → Spring Boot API (port 8080) → RDS MySQL (private subnet); EC2 also calls Amazon Comprehend via an IAM Role — everything inside a single VPC.*

> The frontend is served by Nginx running on the same EC2 as the backend; the **S3 + CloudFront** option is practiced separately in section [5.4](../5.4-S3-CloudFront).