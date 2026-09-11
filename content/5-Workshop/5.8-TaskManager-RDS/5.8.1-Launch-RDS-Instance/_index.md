---
title: "Launch the RDS instance"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.8.1.</b> "
---

## Steps

1. **RDS → Create database** → Engine: **MySQL**, Template: **Free tier**.

![Creating the RDS database](/images/5-Workshop/5.8-TaskManager-RDS/01-rds-create.png)

*The "Create database" page — MySQL, Free tier.*

2. DB instance identifier: `taskmanager-db`. Master username: `admin`, set a strong password and **store it — it cannot be viewed again**.
3. DB instance class: `db.t3.micro`. **Public access: No** (keep RDS private).
4. VPC security group: **Create new**, name `rds-sg`. Initial database name: `taskmanager`.

![RDS instance configuration](/images/5-Workshop/5.8-TaskManager-RDS/02-rds-config.png)

*The DB settings — private, no public access.*

5. **Create database**, wait until the status is **Available**.