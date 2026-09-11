---
title: "Allow EC2 to reach RDS"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.9.2.</b> "
---

## Step 2 — Allow EC2 to reach RDS

1. Open the RDS Security Group `rds-sg` → **Edit inbound rules**.

![Editing the RDS Security Group inbound rules](/images/5-Workshop/5.9-TaskManager-EC2/03-rds-sg-inbound.png)

*Adding the MySQL inbound rule to `rds-sg`.*

2. Add rule **MYSQL/Aurora (port 3306)**, Source: **the EC2 Security Group** (do not open to Anywhere).