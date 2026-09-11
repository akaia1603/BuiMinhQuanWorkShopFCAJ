---
title: "Verify & troubleshooting"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.3.4.</b> "
---

## Expected outcome

- Budget dashboard tracks month-to-date costs
- E-mail notifications at 50% and 80% of the budget, plus an alarm on estimated charges breach

## Troubleshooting

| Issue | Check |
|-------|-------|
| Billing metric has no data | Enable **Receive Billing Alerts** in `us-east-1` before creating the alarm |
| Alarm never fires | Compare against total estimated monthly charges; wait for metric granularity |