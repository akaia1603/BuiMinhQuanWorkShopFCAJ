---
title: "Verify & troubleshooting"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.4.5.</b> "
---

## Step 5 — Verify

1. Wait for the distribution state to become **Enabled**.
2. Open the **Distribution domain name** in the browser and check the page loads.

![Static site loaded over CloudFront HTTPS](/images/5-Workshop/5.4-S3-CloudFront/09-site-https.png)

*Browser loading the page through the CloudFront HTTPS link.*

## Expected outcome

- Static site reachable via the CloudFront URL with an HTTPS padlock
- Public reads granted via the bucket policy only (no object-level ACL changes)

## Troubleshooting

| Issue | Check |
|-------|-------|
| "Access Denied" when opening the URL | Confirm the bucket policy allows public `s3:GetObject` and the index document name matches |
| CloudFront still on "In Progress" | Wait a few minutes for the distribution to become **Enabled** |