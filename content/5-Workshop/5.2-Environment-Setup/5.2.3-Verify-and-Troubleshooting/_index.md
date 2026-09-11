---
title: "Verify & troubleshooting"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.2.3.</b> "
---

## Expected outcome

- Region selector shows `ap-southeast-1` for every console action
- Billing alarms still use `us-east-1` (they are region-specific, see [5.3](../5.3-Cost-Monitoring))

![Console with ap-southeast-1 selected](/images/5-Workshop/5.2-Environment-Setup/03-region-confirmed.png)

*Console with the correct Region `ap-southeast-1` shown in the top-right corner.*

## Troubleshooting

| Issue | Check |
|-------|-------|
| Resources created in a different region | Confirm the region selector top-right before every console action |
| Cross-service calls fail | Services deployed in different regions — keep everything in `ap-southeast-1` |