---
title: "Event 1"
date: 2026-07-25
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# AWS Vietnam Community Meetup — Attendance Report

**Event:** AWS Vietnam Community Meetup — AI Trends & Agentic Architectures on AWS  
**Date:** Saturday, 25/07/2026 – 08:30 to 12:00 (check-in 08:30, program starts 09:00)  
**Location:** AWS Hanoi – 7th Floor, Grand Terra Tower, 36 Cát Linh, Đống Đa, Hanoi  
**Role:** Attendee

## Event overview

A half-day AWS community meetup bringing together AWS Community Heroes, Community Builders, and engineers actively deploying AI in the enterprise. The program covered the latest AI trends and how to apply them on AWS, from open-source AI agents to agent-pattern selection. It also included a tea break & networking session and a Kahoot quiz / lucky draw with AWS Community gifts.

## Program & speakers

| # | Session | Speaker |
|---|---------|---------|
| 1 | **Community Update** — latest activities of the AWS Vietnam community | **Hồ Việt Anh** & **Phong Phạm** |
| 2 | **OpenClaw — The Rise and Practice of Open-Source AI Agents** | **Tuấn Vũ** |
| 3 | **From AI Trends to Business Value** | **Nguyễn Thu** & **Nam La** |
| 4 | **Ship Fast with AI, Not by** | **Henry (Đức) Bùi** |
| 5 | **Selecting the Right AI Agent Pattern on AWS** | **Dũng Lương** |

---

## Session summaries

### Community Update — Hồ Việt Anh & Phong Phạm

The opening session summarized the latest activities of the AWS Vietnam community: study groups, meetups, and the First Cloud AI Journey program. The organizers encouraged attendees to contribute back to the community—by writing blogs, sharing experiences, and mentoring juniors—so that knowledge keeps flowing beyond each individual internship.

---

### Tuấn Vũ — OpenClaw: The Rise and Practice of Open-Source AI Agents

Tuấn Vũ introduced **OpenClaw**, an emerging open-source AI agent framework, and contrasted it with closed, vendor-managed agents. He walked through practical setup, tool integration, and a live demo of an agent that plans and executes multi-step tasks.

**Key points:**
- Open-source agents give teams **transparency and full control** over prompts, tools, and deployment—important for cost and compliance in enterprises.
- An agent is only as capable as its **tool ecosystem** (web search, code execution, file/DB access), so designing a reliable tool layer matters more than the base model.
- Community-driven frameworks iterate quickly, but require evaluating **security and maintenance** before production use.

---

### Nguyễn Thu & Nam La — From AI Trends to Business Value

This session shifted focus from the hype of AI trends to **business value**. The speakers argued that the winning question is not "what can AI do?" but "what business outcome does it unlock and can it be measured?"

**Key points:**
- Frame AI initiatives around **measurable outcomes** (cost saved, time reduced, revenue enabled) rather than model capability alone.
- Start from a real, recurring pain point in the company, then choose the simplest tooling that solves it.
- **Data readiness and change management** are the biggest non-technical blockers to AI adoption.

---

### Henry (Đức) Bùi — Ship Fast with AI, Not by

Henry emphasized using AI to **accelerate delivery** while keeping engineering judgment—"ship fast with AI, not by (AI blindly)". He advocated using AI for scaffolding, code review support, and tedious refactors, while engineers remain responsible for architecture, quality, and security.

**Key points:**
- Use AI as an **accelerator for the boring parts**, reserving human attention for design and correctness.
- Keep **human-in-the-loop** for anything that touches production or data; never merge AI output to production unverified.
- Fast shipping still requires **discipline**: tests, review, and rollback paths.

---

### Dũng Lương — Selecting the Right AI Agent Pattern on AWS

Dũng Lương presented a decision framework for choosing the right **agent pattern on AWS**, matching complexity to the problem rather than reaching for a full agentic platform every time.

**Key points:**
- Understand the spectrum from simple **prompt + tool** calls to **orchestrated multi-agent** systems, and pick the lightest pattern that works.
- On AWS, consider **Amazon Bedrock** agents, the **MCP ecosystem**, and **Lambda-first** orchestration for cost control and observability.
- Design for **observability, guardrails, and auditability**—essential when agents are granted tool access.

---

## Takeaways

- An agent's value comes from its **tool layer and context**, not just the model underneath.
- Always connect AI to **measurable business outcomes**, not feature checkboxes.
- **Human-in-the-loop** remains essential for anything touching production or sensitive data.
- Choose the **simplest agent pattern** that solves the problem, then evolve.
- The AWS Vietnam community is an open, contributor-driven space worth staying involved with long after the internship.

## Personal reflection

This was the first event I attended at the very start of my internship, and it was a great introduction to how AWS connects with the broader ecosystem in Vietnam. The recurring message—build real products, understand what you ship, and tie AI work to business value—set a clear direction for the cloud engineering mindset I wanted to develop during the program. It also introduced me to the community of builders and mentors I could learn from throughout the internship.
