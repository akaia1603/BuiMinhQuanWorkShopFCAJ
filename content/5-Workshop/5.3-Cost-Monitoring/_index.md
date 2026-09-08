---
title: "Cost monitoring — Budgets & CloudWatch"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## Goal

Set up cost monitoring before deploying anything that generates charges, so the bill never exceeds the Free Tier.

## Step 1 — Create an AWS Budget

1. Type `Budgets` in the search bar → **AWS Budgets → Create budget**.
2. Choose **Customize (advanced)** → **Cost budget**.
3. Name: `FCAJ-Budget` — Period: **Monthly** — Budgeted amount: **5 USD**.
4. Add two alert thresholds at **50%** and **80%**, enter the notification e-mail → **Create budget**.

## Step 2 — Enable billing alerts

1. Switch the Region to **`us-east-1` (N. Virginia)**.
2. Go to **Billing Preferences** and enable **Receive Billing Alerts**.

## Step 3 — Create a CloudWatch billing alarm

1. **CloudWatch → Alarms → Billing → Create alarm**.
2. Select the **`EstimatedCharges`** metric, threshold **> 5 USD**.
3. Create an SNS topic that sends an e-mail alert → **Create alarm**.

## Expected outcome

- Budget dashboard tracks month-to-date costs
- E-mail notifications at 50% and 80% of the budget, plus an alarm on estimated charges breach

> **[Screenshot — insert later]:** (1) Budget list showing `FCAJ-Budget`; (2) CloudWatch Alarms showing the alarm in `OK` state; (3) AWS Notifications subscription confirmation e-mail.

## Troubleshooting

| Issue | Check |
|-------|-------|
| Billing metric has no data | Enable **Receive Billing Alerts** in `us-east-1` before creating the alarm |
| Alarm never fires | Compare against total estimated monthly charges; wait for metric granularity |