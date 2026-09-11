---
title: "Wait & copy the Endpoint"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.8.2.</b> "
---

## Steps

1. Create the database and wait until the status is **Available**.
2. In **Connectivity & security**, copy the **Endpoint**.

![RDS instance Available with Endpoint](/images/5-Workshop/5.8-TaskManager-RDS/03-rds-available.png)

*RDS instance page showing status Available and the full Endpoint.*

> **Note:** the RDS instance is running MySQL **8.4** (a test connection returns `Server version: 8.4.9`). If "Initial database name" was left blank, create the database before starting the backend — see Troubleshooting in [5.8.3](5.8.3-Verify-and-Troubleshooting).