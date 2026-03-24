---
type: reference
title: "Advisor Intelligence — Our Tech Stack"
status: active
created: 2026-03-24
updated: 2026-03-24
---

# Our Tech Stack

Tools we use to deliver the Advisor Intelligence service.

## Core Infrastructure

| Tool | Purpose | Cost |
|------|---------|------|
| **Claude Code** | AI development, workflow building, automation | Anthropic subscription |
| **Obsidian** | Knowledge management, client documentation | Free (local) |
| **GitHub** | Version control for code and vault | Free |
| **DigitalOcean VPS** | Run scheduled scripts (prospecting, monitoring) | ~$12/mo |
| **Tailscale** | Secure VPN to VPS | Free tier |

## Client Platform

| Tool | Purpose | Cost |
|------|---------|------|
| **Next.js 16** | Advisor Intelligence web app | — |
| **Supabase** | Database, auth, RLS | Free tier |
| **Vercel** | Hosting and deployment | Free tier |
| **Anthropic SDK** | AI Coach chatbot | Usage-based |

## Research & Intelligence

| Tool | Purpose | Cost |
|------|---------|------|
| **SEC EDGAR/IAPD** | Advisor prospecting data | Free (public) |
| **Brave Search API** | Web research, competitor intel | MCP |
| **Firecrawl** | Web scraping and extraction | MCP |
| **Python** | Data processing, SEC parsing, automation | Free |

## Client-Side Tools We Manage

These are tools we configure/manage within client environments:

| Tool | Clients Using | Our Role |
|------|--------------|----------|
| **Salesforce** | DLK | Build Flows, configure automations, audit |
| **Microsoft 365 / Copilot** | DLK | Advise on usage, integrate with workflows |
| **Schwab Advisor Center** | DLK | Monitor capabilities, integration research |
| **intelliflo redblack** | DLK | Understand drift reports, inform workflows |

## Automation

| System | Schedule | Purpose |
|--------|----------|---------|
| Advisor Prospecting (WF1) | Weekly (cron) | SEC data → filtered prospects → intelligence brief |
| Marketing content agents | Daily 1 PM UTC | LinkedIn + blog + email generation |
| Site monitor | Every 6 hours | Page load health checks |
| Weekly strategy | Sundays 3 PM UTC | Site audit + competitor check |

---

## Related

- [[00-ADVISOR-INTELLIGENCE/INDEX|INDEX]] — Master hub
- [[Service-Playbook]] — How we deliver
