---
title: "Verify SSH & expected outcome"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.6.5.</b> "
---

## Step 5 — Verify SSH access

1. SSH from the personal machine using the key pair.

![Successful SSH terminal session](/images/5-Workshop/5.6-VPC-2Tier/10-ssh-success.png)

*Successful SSH connection to the EC2 instance.*

## Expected outcome

- Public EC2 reachable by SSH (and HTTP) from the internet
- Private subnet has no route to the internet