---
title: "Create a CloudWatch billing alarm"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.3.3.</b> "
---

## Step 3 — Create a CloudWatch billing alarm

1. **CloudWatch → Alarms → Billing → Create alarm**.
2. Select the **`EstimatedCharges`** metric, threshold **> 5 USD**.
3. Create an SNS topic that sends an e-mail alert → **Create alarm**.

![Creating the CloudWatch billing alarm](/images/5-Workshop/5.3-Cost-Monitoring/05-cloudwatch-alarm-create.png)

*Creating a billing alarm on the `EstimatedCharges` metric.*

![Billing alarm in OK state](/images/5-Workshop/5.3-Cost-Monitoring/06-cloudwatch-alarm-ok.png)

*The alarm shows in the `OK` state.*

![AWS Notifications subscription e-mail](/images/5-Workshop/5.3-Cost-Monitoring/07-subscription-email.png)

*The AWS Notifications subscription confirmation e-mail.*