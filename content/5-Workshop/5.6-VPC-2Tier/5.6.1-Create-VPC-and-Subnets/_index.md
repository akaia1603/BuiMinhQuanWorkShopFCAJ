---
title: "Create VPC & subnets"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.6.1.</b> "
---

## Step 1 — VPC & subnets

1. Create a VPC with CIDR `10.0.0.0/16`.

![Creating the VPC](/images/5-Workshop/5.6-VPC-2Tier/02-create-vpc.png)

*Creating a VPC with CIDR `10.0.0.0/16`.*

2. Create two subnets: Public `10.0.1.0/24` and Private `10.0.2.0/24`, placed in two different Availability Zones.

![Creating the subnets](/images/5-Workshop/5.6-VPC-2Tier/03-create-subnets.png)

*The two subnets — public and private.*