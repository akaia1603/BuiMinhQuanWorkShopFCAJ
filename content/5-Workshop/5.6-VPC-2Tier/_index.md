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

> **[Diagram — insert later]:** Internet → IGW → public subnet (EC2); private subnet on its own — both inside the same VPC.

## Step 1 — VPC & subnets

1. Create a VPC with CIDR `10.0.0.0/16`.
2. Create two subnets: Public `10.0.1.0/24` and Private `10.0.2.0/24`, placed in two different Availability Zones.

## Step 2 — Internet Gateway & route table

1. Create an **Internet Gateway** and attach it to the VPC.
2. Create a route table for the public subnet, add route `0.0.0.0/0` → Internet Gateway, associate it with the public subnet.
3. The private subnet keeps the default main route table (no internet path).

## Step 3 — Security Group

1. Create a Security Group allowing **SSH (port 22, source: My IP)** and **HTTP (port 80, source: Anywhere)**.

## Step 4 — Launch EC2

1. Launch an **EC2 instance (Amazon Linux 2023, t2.micro)** in the public subnet.
2. Enable **Auto-assign public IP**, attach the Security Group above.

## Step 5 — Verify SSH access

1. SSH from the personal machine using the key pair.

## Expected outcome

- Public EC2 reachable by SSH (and HTTP) from the internet
- Private subnet has no route to the internet

> **[Screenshot — insert later]:** (1) VPC Resource map; (2) route table configuration; (3) Security Group rules; (4) successful SSH terminal session to EC2.