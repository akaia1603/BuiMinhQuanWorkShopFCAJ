---
title: "Task Manager — EC2 & backend deployment"
date: 2026-09-01
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

## Goal

Deploy the Java Spring Boot backend on an EC2 instance in the same VPC as RDS, and make the database reachable only from that instance.

## Subsections

1. [Launch EC2](5.9.1-Launch-EC2/) — Amazon Linux 2023, t3.micro, in the public subnet.
2. [Allow EC2 to reach RDS](5.9.2-Allow-EC2-to-Reach-RDS/) — port 3306 inbound from the EC2 Security Group only.
3. [Install Java & deploy](5.9.3-Install-Java-and-Deploy/) — build, copy the jar, configure `app.env`, run as a systemd service.
4. [Verify & troubleshooting](5.9.4-Verify-and-Troubleshooting/) — expected outcome and common issues.