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

> **[Diagram — insert later]:** user → CloudFront → S3 bucket.

## Step 1 — Create the S3 bucket

1. Create an S3 bucket (name must be globally unique) in `ap-southeast-1`.
2. Untick **Block all public access** to allow public reads.

## Step 2 — Upload and enable static hosting

1. Upload `index.html` to the bucket.
2. **Properties → Static website hosting → Enable**, Index document: `index.html`.

## Step 3 — Bucket policy

1. **Permissions → Bucket policy**, add a policy that allows `s3:GetObject` publicly on every object.

## Step 4 — CloudFront distribution

1. Create a **CloudFront Distribution**, Origin domain pointing to the bucket created earlier.
2. Viewer protocol policy: **Redirect HTTP to HTTPS**.

## Step 5 — Verify

1. Wait for the distribution state to become **Enabled**.
2. Open the **Distribution domain name** in the browser and check the page loads.

## Expected outcome

- Static site reachable via the CloudFront URL with an HTTPS padlock
- Public reads granted via the bucket policy only (no object-level ACL changes)

> **[Screenshot — insert later]:** (1) S3 bucket properties showing Static website hosting: Enabled; (2) CloudFront distribution with status Enabled; (3) browser loading the page through the CloudFront HTTPS link.