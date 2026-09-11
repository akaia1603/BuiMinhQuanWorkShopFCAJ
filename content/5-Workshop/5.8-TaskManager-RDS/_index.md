---
title: "Task Manager — RDS MySQL"
date: 2026-09-01
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

## Goal

Provision the MySQL database on RDS, kept private so only the EC2 backend can reach it.

## Subsections

1. [Launch the RDS instance](5.8.1-Launch-RDS-Instance/) — MySQL free tier, `taskmanager-db`.
2. [Wait & copy the Endpoint](5.8.2-Wait-and-Copy-Endpoint/) — get the DB address.
3. [Verify & troubleshooting](5.8.3-Verify-and-Troubleshooting/) — expected outcome and common issues.