---
type: reference
title: "Accumulated Learnings"
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
---

# Accumulated Learnings

> Living document. Distilled insights across all sessions. Not a log — a knowledge base. Organized by topic.

## Selling to RIAs

- RIAs buy from relationships, not cold outreach. 90% of first clients come from existing network. (2026-03-16)
- "We have money, we don't have time" is the universal pain statement. Lead with time savings, not cost savings. (2026-03-23, DLK)
- Don't sell AI tools — sell outcomes. Advisors don't care about the tech, they care about getting time back. (2026-03-16)
- "Fair is what's negotiated" — Don signaled price acceptance with this phrase. Good buying signal to watch for. (2026-03-23)
- The "W" (win / case study) is worth more than the dollar amount on the first engagement. Build the proof. (2026-03-23, Don's advice)
- 58% of advisors report losing business due to inferior tech. 92% of clients would switch firms over bad tech. Use these in pitch. (2026-03-24)
- Wirehouses are a dead end for consulting — FINRA rules 3270 and 3110 block outside consultants. Personal coaching only. (2026-03-16)

## Salesforce for RIAs

- Most RIAs use Salesforce as a glorified Rolodex. 60–70% of paid features go unused. This IS our value proposition. (2026-03-23)
- Process Builder and Workflow Rules were retired Dec 31, 2025. All new automation must use Flow Builder. (2026-03-23)
- "Do not buy Salesforce without a pre-made overlay partner" — industry consensus. Raw FSC requires dedicated admin. (2026-03-23)
- Schwab Advisor Center has a free AppExchange integration — daily batch sync of account data. Check if DLK has it. (2026-03-23)
- API access requires Enterprise edition minimum. Needed for n8n webhook integration. Confirm DLK's edition in Week 1. (2026-03-24)

## AI Tool Landscape

- Hazel caused a $130B selloff in wealth management stocks at launch. The market takes advisor AI seriously. (2026-03-24)
- Jump has 22.68% market share (T3 2026) — the clear leader. But XYPN gave it 3.5/5 on accuracy. Not plug-and-play. (2026-03-24)
- Agentforce costs $62,700+/year for 11 users. Our full consulting is $17,500/year. 3.5x cost advantage. (2026-03-24)
- Zocks recommended for DLK because no-audio-recording = compliance-first. Don will appreciate this. (2026-03-23)
- 95% of GenAI pilots fail to deliver P&L impact (MIT). Guided implementation succeeds at 2x the rate of DIY. This is our strongest data point. (2026-03-24)

## Technical Architecture

- n8n on DigitalOcean VPS with Docker Compose is the right middleware choice. Visual workflows = compliance transparency. (2026-03-24)
- Use PostgreSQL backend for n8n (not SQLite). Production requirement. (2026-03-24)
- Tailscale for admin UI access — no public exposure of n8n dashboard. (2026-03-24)
- Nginx reverse proxy for Salesforce webhook endpoints on the VPS. (2026-03-24)
- SEC IAPD bulk data best accessed via monthly IA Information Report from data.gov. sec-api.io for precision filtering. (2026-03-23)
- Every AI call needs DLK-specific system prompts capturing tone, client base, investment philosophy, compliance boundaries. (2026-03-24)

## Client Management

- Hub-and-spoke vault architecture works well. Client planet (DLK-HUB.md) as entry point, with People/, Workflows/, Compliance/, Tech-Stack/ spokes. (2026-03-23)
- Team member interviews (15–20 min each) are critical for understanding real needs vs stated needs. Mark's needs are very different from Don's. (2026-03-23)
- Don as CEO/CCO thinks strategically (M&A, compliance). Mark as CFP thinks operationally (daily workflow, task management). Map deliverables to both. (2026-03-23)
- "Trust and verify" is Don's operating philosophy. Everything we build needs an audit trail he can inspect. (2026-03-23)

## Business Operations

- Obsidian MCP list-available-vaults hangs frequently. Write vault files via bash as fallback. (2026-03-13)
- Cron scripts require active OAuth session. Re-login with `claude /login` if they fail. All scripts failed March 14–16 due to token expiration. (2026-03-16)
- Build verification can OOM on 8GB system. Pre-existing limitation. (2026-03-16)
- E&O insurance is critical before taking on clients. Apply via Next Insurance ASAP. (2026-03-24)
- EIN blocks everything financial (banking, Stripe, invoicing). Priority #1 for infrastructure. (2026-03-24)

## Content & Marketing

- Dan Skiles conversation was the catalyst for the consulting pivot. "Head of AI is a new division in everybody's company." (2026-03-16)
- No one occupies the intersection of AI expertise + advisor industry knowledge. This is genuine white space. (2026-03-16)
- LinkedIn content pivot needed: from "AI toolkit" messaging to "AI consulting" positioning. (2026-03-16)
- 3-5 posts/week on LinkedIn builds inbound leads over 3-6 months. Play the long game. (2026-03-16)
