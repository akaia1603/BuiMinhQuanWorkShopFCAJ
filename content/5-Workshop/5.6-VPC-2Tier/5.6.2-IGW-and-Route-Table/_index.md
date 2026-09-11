---
title: "Internet Gateway & route table"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.6.2.</b> "
---

## Step 2 — Internet Gateway & route table

1. Create an **Internet Gateway** and attach it to the VPC.

![Attaching the Internet Gateway](/images/5-Workshop/5.6-VPC-2Tier/04-create-igw.png)

*The Internet Gateway attached to the VPC.*

2. Create a route table for the public subnet, add route `0.0.0.0/0` → Internet Gateway, associate it with the public subnet.
3. The private subnet keeps the default main route table (no internet path).

![Route table configuration](/images/5-Workshop/5.6-VPC-2Tier/05-route-table.png)

*The route table with `0.0.0.0/0` → Internet Gateway.*