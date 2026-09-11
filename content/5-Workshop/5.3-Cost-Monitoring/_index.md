---
title: "Cost monitoring — Budgets & CloudWatch"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## Goal

Set up cost monitoring before deploying anything that generates charges, so the bill never exceeds the Free Tier.

## Subsections

1. [Create an AWS Budget](5.3.1-Create-AWS-Budget/) — `FCAJ-Budget`, 5 USD/month with 50%/80% alerts.
2. [Enable billing alerts](5.3.2-Enable-Billing-Alerts/) — `Receive Billing Alerts` in `us-east-1`.
3. [Create a CloudWatch billing alarm](5.3.3-Create-CloudWatch-Alarm/) — alarm on `EstimatedCharges` > 5 USD.
4. [Verify & troubleshooting](5.3.4-Verify-and-Troubleshooting/) — expected outcome and common issues.