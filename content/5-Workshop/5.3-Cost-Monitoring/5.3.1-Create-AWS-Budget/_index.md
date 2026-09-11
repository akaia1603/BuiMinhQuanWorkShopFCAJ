---
title: "Create an AWS Budget"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.3.1.</b> "
---

## Step 1 — Create an AWS Budget

1. Type `Budgets` in the search bar → **AWS Budgets → Create budget**.
2. Choose **Customize (advanced)** → **Cost budget**.

![Opening AWS Budgets](/images/5-Workshop/5.3-Cost-Monitoring/01-budget-menu.png)

*The AWS Budgets page where you create a budget.*

3. Name: `FCAJ-Budget` — Period: **Monthly** — Budgeted amount: **5 USD**.

![Creating the budget with name and amount](/images/5-Workshop/5.3-Cost-Monitoring/02-budget-create.png)

*Budget configuration: `FCAJ-Budget`, Monthly, 5 USD.*

4. Add two alert thresholds at **50%** and **80%**, enter the notification e-mail → **Create budget**.

![Budget list showing FCAJ-Budget](/images/5-Workshop/5.3-Cost-Monitoring/03-budget-list.png)

*The budget list showing `FCAJ-Budget`.*