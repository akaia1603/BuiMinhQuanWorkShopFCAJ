---
title: "Week 6 Worklog"
date: 2026-08-29
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Complete the capstone project (async post-match processing, VPC hardening).
* Complete the AWS workshop lab content.

**Period:** 29/08/2026 – 04/09/2026

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Implement async post-match processing: DynamoDB Streams → MatchAnalytics Lambda | 31/08/2026 | 31/08/2026 | |
| 3 | - Move MatchMaker Lambda to private subnets with VPC endpoints (no NAT); install CodeDeploy agent on the EC2 fleet | 01/09/2026 | 01/09/2026 | |
| 4 | - Final integration testing: matchmaking → gameplay → match finish → analytics | 02/09/2026 | 02/09/2026 | |
| 5 | - Complete workshop sections: S3 VPC endpoints, on-prem simulation, cleanup (documented with screenshots, cancel before delete) | 03/09/2026 | 03/09/2026 | FCAJ workshop template |
| 6 | - Complete capstone deliverables and hand off workshop lab documentation to the team | 04/09/2026 | 04/09/2026 | |

### Week 6 Achievements:

* Deployed the **Flow E** async pipeline: `ActiveMatches` DynamoDB Stream → `FightingGameMatchAnalytics` Lambda → `MatchAnalytics` table.
* Reconfigured the MatchMaker into private subnets with DynamoDB gateway and EC2/CloudWatch interface endpoints.
* Installed and configured the CodeDeploy agent on game server instances.
* Verified the full game lifecycle: login → queue → match → WebSocket gameplay → finished match recorded in DynamoDB.
* Completed all workshop lab write-ups including VPC Gateway endpoints, PrivateLink interface endpoints, and DNS simulation.
* Documented teardown screenshots (confirmation screens only, no actual deletion).
