---
type: reference
title: "Advisor Intelligence — Our Tech Stack"
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
---

# Our Tech Stack

> Last Updated: 2026-03-24. Tools we use to deliver the Advisor Intelligence service.

## Core Infrastructure

| Tool | Purpose | Cost |
|------|---------|------|
| **Claude Code** | AI development, workflow building, automation | Anthropic subscription |
| **Obsidian** | Knowledge management, client documentation | Free (local) |
| **GitHub** | Version control for code and vault | Free |
| **DigitalOcean VPS** | Run n8n, scheduled scripts, monitoring | ~$12–$24/mo |
| **Tailscale** | Secure VPN to VPS | Free tier |

## Client Platform

| Tool | Purpose | Cost |
|------|---------|------|
| **Next.js 16** | Advisor Intelligence web app | — |
| **Supabase** | Database, auth, RLS | Free tier |
| **Vercel** | Hosting and deployment | Free tier |
| **Anthropic SDK** | AI Coach chatbot | Usage-based |

## n8n Orchestration Layer (NEW — DLK)

n8n is the middleware that connects client systems to AI capabilities. Self-hosted for data control and compliance.

### Deployment

| Component | Details |
|-----------|---------|
| **Hosting** | DigitalOcean VPS via Docker Compose |
| **Database** | PostgreSQL backend (not SQLite — production-grade) |
| **Access** | Tailscale for admin UI (no public exposure) |
| **Webhooks** | Nginx reverse proxy for Salesforce webhook endpoints |
| **Version control** | All workflow JSON stored in vault |

### Why n8n

- **Visual workflow builder** — compliance transparency for Don (can show "here's exactly what happens")
- **Native Salesforce nodes** — read/write CRM data without custom code
- **HTTP nodes** — call Claude API, SEC EDGAR, any REST endpoint
- **Cron scheduling** — automated weekly reports, daily digests
- **Error workflows** — email Cri on any failure
- **Self-hosted** — client data never leaves our infrastructure
- **Cost** — ~$12–$24/month vs $1,000+/month for enterprise iPaaS

### Architecture Per Workflow

| Workflow | Trigger | Flow |
|----------|---------|------|
| **WF1 (Prospecting)** | Cron (weekly) | SEC data fetch → Python processing → Claude API enrichment → email delivery → Salesforce prospect creation |
| **WF2 (Onboarding)** | Salesforce webhook | Core automation native in Salesforce Flows, AI content generation via n8n webhook calling Claude API |
| **WF3 (Review Cycle)** | Salesforce scheduled flow | Salesforce triggers/escalation, n8n for AI email drafting and meeting note processing |

### Prompt Engineering

DLK-specific system prompts for every AI call. Must capture:
- DLK's tone and communication style
- Client base characteristics
- Investment philosophy (individual stocks, not just funds)
- Compliance boundaries (Don's "trust and verify")

Prompt library in vault:
- System-Prompt-Base
- Prompt-Review-Email
- Prompt-Meeting-Brief
- Prompt-Meeting-Summary
- Prompt-Prospecting-Brief
- Prompt-Welcome-Email

## Research & Intelligence

| Tool | Purpose | Cost |
|------|---------|------|
| **SEC EDGAR/IAPD** | Advisor prospecting data | Free (public) |
| **Brave Search API** | Web research, competitor intel | MCP |
| **Firecrawl** | Web scraping and extraction | MCP |
| **Python** | Data processing, SEC parsing, automation | Free |

## Client-Side Tools We Manage

| Tool | Clients Using | Our Role |
|------|--------------|----------|
| **Salesforce** | DLK | Build Flows, configure automations, audit. See [[15-SALESFORCE/FSC-Features|FSC Features]]. |
| **Microsoft 365 / Copilot** | DLK | Advise on usage, integrate with workflows |
| **Schwab Advisor Center** | DLK | Monitor capabilities, integration research |
| **intelliflo redblack** | DLK | Understand drift reports, inform workflows |

## Meeting Notes Pipeline (DLK)

| Component | Tool | Notes |
|-----------|------|-------|
| **Recording** | Zocks (recommended) | No audio recording = compliance-first. See [[10-INDUSTRY/Competitor-Tools/Zocks|Zocks profile]]. |
| **Alternative** | Otter.ai on phone | For in-person meetings |
| **Processing** | n8n + Claude API | Structured extraction from transcripts |
| **Destination** | Salesforce CRM | Notes, tasks, and follow-ups auto-populated |

## Automation Schedule

| System | Schedule | Purpose |
|--------|----------|---------|
| WF1 Prospecting | Weekly (cron) | SEC data → filtered prospects → intelligence brief |
| Marketing content agents | Daily 1 PM UTC | LinkedIn + blog + email generation |
| Site monitor | Every 6 hours | Page load health checks |
| Weekly strategy | Sundays 3 PM UTC | Site audit + competitor check |

---

## Related

- [[00-ADVISOR-INTELLIGENCE/INDEX|INDEX]] — Master hub
- [[Service-Playbook]] — How we deliver
- [[20-CLIENTS/DLK/Tech-Stack/Current-Stack|DLK Current Stack]]
- [[Business-Infrastructure]] — Legal, banking, insurance
