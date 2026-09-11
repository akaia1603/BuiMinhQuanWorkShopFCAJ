---
title: "Task Manager — EC2 & backend deployment"
date: 2026-09-01
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

## Goal

Deploy the Java Spring Boot backend on an EC2 instance in the same VPC as RDS, and make the database reachable only from that instance.

## Step 1 — Launch EC2

1. Launch an EC2 instance (**Amazon Linux 2023, t3.micro**) in the same VPC as the RDS, in a public subnet.
2. Security Group: open **port 22 (source: My IP)** and **port 8080 (source: Anywhere)** (open **port 80** later when deploying the frontend in [5.11](5.11-TaskManager-Frontend/)).

## Step 2 — Allow EC2 to reach RDS

1. Open the RDS Security Group `rds-sg` → **Edit inbound rules**.
2. Add rule **MYSQL/Aurora (port 3306)**, Source: **the EC2 Security Group** (do not open to Anywhere).

## Step 3 — Install Java and deploy

1. SSH into the EC2 instance.
2. Install Java 17: `sudo dnf install -y java-17-amazon-corretto-devel`.
3. Build locally: `mvn clean package -DskipTests`, copy the `.jar` to EC2 with `scp`.
4. Create `app.env` with the environment variables: `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `AWS_REGION`, `AI_ENABLED` (`JWT_SECRET` must be **at least 32 characters**).
5. Create a `systemd` service so the app restarts automatically when EC2 reboots.
6. Start the service and watch the logs: `journalctl -u taskmanager -f`.

## Expected outcome

- Backend running as a systemd service and auto-starting on reboot
- `POST /api/auth/register` returns a JWT token
- `GET /actuator/health` returns `{"status":"UP"}` when checked with `curl`

## Troubleshooting

| Issue | Fix |
|-------|-----|
| EC2 cannot connect to RDS | Check the RDS Security Group inbound rule for port 3306 — source must be the EC2 Security Group, not public |
| Login returns `403` and the log shows `SignatureException: JWT signature does not match` | `JWT_SECRET` in `app.env` is too short (< 32 characters). Use a string of at least 32 characters and restart the service |
| Backend runs but with wrong config (issued tokens are rejected) | The properties are read under the `app.*` prefix (e.g. `@Value("${app.jwt.secret}")`). When running `java -jar`, pass `--app.jwt.secret`, `--app.aws.region`, `--app.ai.enabled` — not `--jwt.secret`, `--aws.region`, `--ai.enabled` |
| App fails to start with `Unknown database 'taskmanager'` | The database was not created on RDS — see the Troubleshooting in [5.8](5.8-TaskManager-RDS/) |

> **[Screenshot — insert later]:** (1) EC2 instance running; (2) service log showing "Started TaskManagerApiApplication"; (3) `POST /api/auth/register` returns a JWT token.