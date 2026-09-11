---
title: "Static website — S3 + CloudFront"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

## Goal

Host a static website (e.g. the frontend bundle) on S3 and serve it through CloudFront over HTTPS.

## Architecture

![S3 + CloudFront architecture diagram](/images/5-Workshop/5.4-S3-CloudFront/01-diagram.png)

*Diagram: user → CloudFront → S3 bucket.*

## Subsections

1. [Create the S3 bucket](5.4.1-Create-S3-Bucket/) — globally unique name, public reads allowed.
2. [Enable static hosting](5.4.2-Enable-Static-Hosting/) — upload `index.html`, enable Static website hosting.
3. [Set the bucket policy](5.4.3-Set-Bucket-Policy/) — public `s3:GetObject`.
4. [Create the CloudFront distribution](5.4.4-Create-CloudFront-Distribution/) — origin pointing to the bucket.
5. [Verify & troubleshooting](5.4.5-Verify-and-Troubleshooting/) — HTTPS access via CloudFront.