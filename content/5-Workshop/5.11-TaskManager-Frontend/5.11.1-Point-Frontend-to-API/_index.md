---
title: "Point the frontend to the API"
date: 2026-09-01
weight: 1
chapter: false
pre: " <b>5.11.1.</b> "
---

## Step 1 — Point the frontend to the API

1. Edit `API_BASE` in `frontend/js/config.js` to the real EC2 address: `http://<EC2-Public-IP>:8080`.

![Editing API_BASE in config.js](/images/5-Workshop/5.11-TaskManager-Frontend/01-config-js.png)

*`API_BASE` set to the EC2 public address.*