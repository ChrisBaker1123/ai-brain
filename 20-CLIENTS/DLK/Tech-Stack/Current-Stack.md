---
type: reference
title: "DLK Current Tech Stack"
status: active
created: 2026-03-24
client: DLK
---

# DLK Current Tech Stack

## Confirmed Tools (from transcript + research)

| Category | Tool | Used By | Status |
|----------|------|---------|--------|
| **CRM** | Salesforce | All | Massively underutilized — primary CRM functions only |
| **Custodian** | Schwab Advisor Center | Mark, Brian | Daily alerts, account management, trading |
| **Rebalancing** | intelliflo redblack | Mark, Brian | Drift reports, rebalancing instructions |
| **Office Suite** | Microsoft 365 | All | Email, docs, calendar |
| **AI (experimental)** | Microsoft Copilot | Mark | Task recognition, To Do integration — experimenting since Meeting 1 |
| **Email Marketing** | Mailchimp | Admin | Newsletter distribution |
| **Website** | WordPress (BlueHost) | — | dlkinvest.com, Cloudflare CDN |
| **Client Portal** | Schwab (likely) | Clients | dlkinvest.com/client-login/ |

## Not Using (Gaps)

| Category | Gap | Opportunity |
|----------|-----|-------------|
| **AI tools** | No dedicated AI beyond Copilot experimentation | Advisor Intelligence fills this |
| **Meeting notes** | No transcription tool | Recommend Otter.ai or Fireflies for in-person |
| **Compliance tech** | Manual processes | AI-assisted compliance checks |
| **Financial planning** | Not mentioned — ask in interviews | Likely eMoney or similar |
| **Document management** | Not mentioned | May be using SharePoint via M365 |
| **Scheduling** | Not mentioned | Calendly or similar for client scheduling? |

## Salesforce Details (TBD — Week 1 Audit)

- **Edition**: Unknown — need to confirm (determines available features)
- **Custom objects**: Unknown
- **Existing automations**: Unknown
- **API access**: Unknown
- **Financial Services Cloud**: Unlikely at this firm size, but ask

→ Full audit: [[20-CLIENTS/DLK/Tech-Stack/Salesforce-Audit|Salesforce Audit]]

## Integration Map

```
Schwab Advisor Center
  ├── Alerts → Mark (manual check each morning)
  ├── Account data → Salesforce (manual entry by Mark)
  └── Trading → Brian (manual execution)

intelliflo redblack
  ├── Drift reports → Mark (manual check each morning)
  └── Rebalancing instructions → Brian (manual/email from Mark)

Salesforce
  ├── Contacts/Clients → manual entry
  ├── Reviews → manual tracking
  ├── Pipeline → not using
  └── Automations → none currently

Microsoft 365
  ├── Email → all communication
  ├── Calendar → meeting scheduling
  ├── Copilot → Mark experimenting
  └── To Do → Mark testing task creation via Copilot

Mailchimp
  └── Newsletter → client distribution
```

## Key Insight

Don: "We know it does more than it is doing right now. We just don't know how to do this."

The biggest opportunity is Salesforce. It's already paid for and has the data. They just need workflows built.

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Tech-Stack/Salesforce-Audit|Salesforce Audit]]
- [[20-CLIENTS/DLK/Tech-Stack/Integration-Map|Integration Map]]
