---
title: "Install Java & deploy"
date: 2026-09-01
weight: 3
chapter: false
pre: " <b>5.9.3.</b> "
---

## Step 3 — Install Java and deploy

1. SSH into the EC2 instance.
2. Install Java 17: `sudo dnf install -y java-17-amazon-corretto-devel`.

![Installing Java 17 on EC2](/images/5-Workshop/5.9-TaskManager-EC2/04-install-java.png)

*Java 17 installed on the EC2 instance.*

3. Build locally: `mvn clean package -DskipTests`, copy the `.jar` to EC2 with `scp`.
4. Create `app.env` with the environment variables: `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `AWS_REGION`, `AI_ENABLED` (`JWT_SECRET` must be **at least 32 characters**).
5. Create a `systemd` service so the app restarts automatically when EC2 reboots.
6. Start the service and watch the logs: `journalctl -u taskmanager -f`.

![Backend service log](/images/5-Workshop/5.9-TaskManager-EC2/05-backend-log.png)

*Service log showing "Started TaskManagerApiApplication".*