---
title: "Launch EC2"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.9.1.</b> "
---

## Step 1 — Launch EC2

1. Launch an EC2 instance (**Amazon Linux 2023, t3.micro**) in the same VPC as the RDS, in a public subnet.

![Launching the EC2 instance](/images/5-Workshop/5.9-TaskManager-EC2/01-ec2-launch.png)

*Launching an Amazon Linux 2023 t3.micro instance.*

2. Security Group: open **port 22 (source: My IP)** and **port 8080 (source: Anywhere)** (open **port 80** later when deploying the frontend in [5.11](../5.11-TaskManager-Frontend)).

![EC2 instance running](/images/5-Workshop/5.9-TaskManager-EC2/02-ec2-running.png)

*The backend EC2 instance in the Running state.*