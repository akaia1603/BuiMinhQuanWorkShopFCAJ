---
title: "VPC 2-tier"
date: 2026-09-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

## Goal

Design a 2-tier VPC: a public subnet for the internet-facing EC2 and a private subnet reserved for the database tier — the same model reused by the Task Manager project.

## Architecture

![VPC 2-tier architecture diagram](/images/5-Workshop/5.6-VPC-2Tier/01-diagram.png)

*Diagram: Internet → IGW → public subnet (EC2); private subnet on its own — both inside the same VPC.*

## Subsections

1. [Create VPC & subnets](5.6.1-Create-VPC-and-Subnets/) — `10.0.0.0/16`, public `10.0.1.0/24`, private `10.0.2.0/24`.
2. [Internet Gateway & route table](5.6.2-IGW-and-Route-Table/) — `0.0.0.0/0` → IGW for the public subnet.
3. [Create the Security Group](5.6.3-Create-Security-Group/) — SSH and HTTP rules.
4. [Launch EC2](5.6.4-Launch-EC2/) — Amazon Linux 2023, t2.micro, public subnet.
5. [Verify SSH & expected outcome](5.6.5-Verify-SSH-and-Outcome/) — connect and confirm the design.