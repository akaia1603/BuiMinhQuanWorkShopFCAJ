---
title: "Week 5 Worklog"
date: 2026-08-22
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Design the 2-tier VPC and set up the network foundation for the main project.
* Provision RDS MySQL and deploy the Task Manager Spring Boot backend on EC2.

**Period:** 22/08/2026 – 28/08/2026

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Design the VPC 2-tier: VPC `10.0.0.0/16`, public subnet `10.0.1.0/24` and private subnet `10.0.2.0/24` in two AZs <br> - Create the Internet Gateway, public route table and Security Group (SSH My IP + HTTP) | 24/08/2026 | 24/08/2026 | AWS VPC docs |
| 3 | - Launch an EC2 (Amazon Linux 2023, t2.micro) in the public subnet and verify SSH access | 25/08/2026 | 25/08/2026 | |
| 4 | - Design the Task Manager database (users/projects/tasks) and technology stack <br> - Create RDS MySQL `taskmanager-db` (Free tier, db.t3.micro, public access: No) | 26/08/2026 | 26/08/2026 | AWS RDS docs |
| 5 | - Add inbound 3306 to the RDS Security Group with the EC2 Security Group as source <br> - Build the Spring Boot project locally (`mvn clean package -DskipTests`) | 27/08/2026 | 27/08/2026 | Spring Boot docs |
| 6 | - Copy the `.jar` to EC2 via scp; create `app.env` and a systemd service <br> - **Test:** register via `POST /api/auth/register` and confirm RDS connectivity | 28/08/2026 | 28/08/2026 | |

### Week 5 Achievements:

* Built a secure 2-tier VPC matching the architecture used by the main project.
* Provisioned a private RDS MySQL instance reachable only from the EC2 Security Group.
* Deployed the Task Manager Spring Boot backend on EC2 as a systemd service with JWT registration working against RDS.
* Applied least-privilege Security Group rules for the database tier (no public 3306).