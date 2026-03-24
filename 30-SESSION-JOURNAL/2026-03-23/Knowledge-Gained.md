---
date: 2026-03-23
tags: [session, knowledge, dlk]
---

# Knowledge Gained: 2026-03-23

## SEC IAPD Data Access

- Best bulk access: Monthly IA Information Report from data.gov (free, comprehensive)
- sec-api.io: Paid service for precision filtering and structured queries — needs evaluation
- Individual firm lookups: adviserinfo.sec.gov (CRD number lookup)
- DLK CRD: 149096

## Salesforce Automation State (2026)

- Process Builder and Workflow Rules retired December 31, 2025
- All new automation must use Flow Builder
- Record-Triggered Flows replace Process Builder
- Scheduled Flows replace time-based Workflow Rules
- Platform Events for real-time integration with external systems

## Zocks as Meeting Tool Recommendation

- No audio recording = dramatically simpler compliance
- Don's "trust and verify" philosophy aligns with no-recording approach
- Competitors (Jump, Hazel) all record and store audio — creates compliance surface area
- Zocks $100+/seat, Otter.ai alternative for in-person (phone recording)

## Hub-and-Spoke Vault Architecture

- "Sun" (00-ADVISOR-INTELLIGENCE) holds business-level knowledge
- "Planets" (20-CLIENTS/[name]) hold client-specific knowledge
- "Rings" (10-INDUSTRY, 15-SALESFORCE) hold shared domain knowledge
- Each planet is self-contained: HUB.md entry → People, Workflows, Compliance, Tech-Stack, Deliverables
- Scales naturally: add a client = add a planet

## n8n as Middleware Choice

- Self-hosted Docker Compose on DigitalOcean VPS (~$12/mo)
- Visual workflow builder — can show Don exactly what happens
- Native Salesforce nodes (read/write without custom code)
- PostgreSQL backend for production reliability
- Tailscale for secure admin access
- Error workflows with email notifications

---

## Related

- [[30-SESSION-JOURNAL/2026-03-23/Session-Log|Session Log]]
- [[30-SESSION-JOURNAL/LEARNINGS|Accumulated Learnings]]
