---
title: "Task Manager — RDS MySQL"
date: 2026-09-01
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

## Goal

Provision the MySQL database on RDS, kept private so only the EC2 backend can reach it.

## Steps

1. **RDS → Create database** → Engine: **MySQL**, Template: **Free tier**.
2. DB instance identifier: `taskmanager-db`. Master username: `admin`, set a strong password and **store it — it cannot be viewed again**.
3. DB instance class: `db.t3.micro`. **Public access: No** (keep RDS private).
4. VPC security group: **Create new**, name `rds-sg`. Initial database name: `taskmanager`.
5. **Create database**, wait until the status is **Available**.
6. In **Connectivity & security**, copy the **Endpoint**.

## Expected outcome

- RDS instance `taskmanager-db` in `Available` state
- Private — no public access; connections allowed only from the EC2 Security Group

> **[Screenshot — insert later]:** RDS instance page showing status Available and the full Endpoint.