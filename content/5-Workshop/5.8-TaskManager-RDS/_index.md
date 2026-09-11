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

> **Note:** the RDS instance is running MySQL **8.4** (a test connection returns `Server version: 8.4.9`). If "Initial database name" was left blank, create the database before starting the backend — see Troubleshooting below.

## Expected outcome

- RDS instance `taskmanager-db` in `Available` state
- Private — no public access; connections allowed only from the EC2 Security Group
- The `taskmanager` database exists and can be reached with a MySQL/MariaDB client

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Backend fails to start with `Unknown database 'taskmanager'` | "Initial database name" was left blank during RDS creation, so the database does not exist. Install the client on EC2: `sudo yum install -y mariadb105`, connect with `mysql -h <endpoint> -u admin -p`, then create it: `CREATE DATABASE taskmanager; SHOW DATABASES;` |

> **[Screenshot — insert later]:** RDS instance page showing status Available and the full Endpoint.