---
title: "Verify & troubleshooting"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.8.3.</b> "
---

## Expected outcome

- RDS instance `taskmanager-db` in `Available` state
- Private — no public access; connections allowed only from the EC2 Security Group
- The `taskmanager` database exists and can be reached with a MySQL/MariaDB client

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Backend fails to start with `Unknown database 'taskmanager'` | "Initial database name" was left blank during RDS creation, so the database does not exist. Install the client on EC2: `sudo yum install -y mariadb105`, connect with `mysql -h <endpoint> -u admin -p`, then create it: `CREATE DATABASE taskmanager; SHOW DATABASES;` |