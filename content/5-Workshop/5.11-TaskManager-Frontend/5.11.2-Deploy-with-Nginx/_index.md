---
title: "Deploy with Nginx"
date: 2026-09-01
weight: 2
chapter: false
pre: " <b>5.11.2.</b> "
---

## Step 2 — Deploy the frontend with Nginx on EC2

1. Install Nginx on EC2: `sudo yum install -y nginx`.

![Installing Nginx on EC2](/images/5-Workshop/5.11-TaskManager-Frontend/02-nginx-install.png)

*Nginx installed on EC2.*

2. Copy the whole `frontend/` folder into `/usr/share/nginx/html/`, create a server block in `/etc/nginx/conf.d/taskmanager.conf` (listen **80**, `root /usr/share/nginx/html`, `try_files $uri $uri/ /index.html;`).

![Nginx server block configuration](/images/5-Workshop/5.11-TaskManager-Frontend/03-nginx-conf.png)

*The `taskmanager.conf` server block.*

3. Start and enable it: `sudo systemctl start nginx && sudo systemctl enable nginx`.
4. Open **port 80** in the EC2 Security Group (Custom TCP, source `0.0.0.0/0`).

![Security Group with port 80 open](/images/5-Workshop/5.11-TaskManager-Frontend/04-sg-port80.png)

*Port 80 open for HTTP in the EC2 Security Group.*

> **Design note:** serving the frontend with Nginx on the same EC2 as the backend keeps them close together and reduces cost for a small project; the **S3 + CloudFront** option is practiced separately in section [5.4](../5.4-S3-CloudFront).