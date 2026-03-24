---
type: reference
title: "Salesforce Financial Services Cloud Features"
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
---

# Salesforce for RIAs — Feature Reference

> Last Updated: 2026-03-24. Populated with research findings. Updated as we learn more from DLK's actual edition.

## Pricing (2026)

| Edition | Per User/Month | Annual (6 users) | Annual (11 users) |
|---------|---------------|------------------|-------------------|
| Essentials | $25 | $1,800 | $3,300 |
| Professional | $80 | $5,760 | $10,560 |
| Enterprise | $165 | $11,880 | $21,780 |
| FSC (Financial Services Cloud) | $325 | $23,400 | $42,900 |
| Sales Cloud Enterprise | ~$165 | $11,880 | $21,780 |

### Overlay Pricing (Alternatives to Raw SF)

| Platform | Price | Best For | Notes |
|----------|-------|----------|-------|
| **XLR8 (Concenter)** | $75/user/month (includes SF license) | Solo to mid-size RIAs | Lower complexity, good without dedicated SF admin |
| **Practifi** | $150–$250/user/month | Growing multi-advisor firms | Robust workflows, compliance tracking, eMoney integration |
| **Salentica Elements** | $90/user/month | Enterprise RIAs (10+ users) | Deep customization |

**Advisor community consensus**: "Do not buy Salesforce without a pre-made overlay partner." Raw SF FSC requires significant admin expertise.

**Key stat**: 40% of Barron's Top 20 RIAs use FSC.

### Implementation Costs

- Typical implementation: $25,000 (small RIA) to $200,000+ (mid-size) (Vantage Point estimates)
- Salesforce consultants: $150–$250/hour (ShellBlack, Vantage Point)
- DLK's likely total SF spend: $15,000–$45,000/year depending on edition

## Editions and Key Features

| Feature | Essentials | Professional | Enterprise | FSC |
|---------|-----------|-------------|-----------|-----|
| Contacts/Accounts | ✅ | ✅ | ✅ | ✅ |
| Record-Triggered Flows | ❌ | ✅ | ✅ | ✅ |
| Scheduled Flows | ❌ | ✅ (limited) | ✅ | ✅ |
| Custom Objects | ❌ | ✅ (limited) | ✅ | ✅ |
| API Access | ❌ | ❌ | ✅ | ✅ |
| Lightning App Builder | ✅ | ✅ | ✅ | ✅ |
| Reports & Dashboards | Basic | ✅ | ✅ | ✅ |
| Action Plan Templates | ❌ | ❌ | ❌ | ✅ |
| Financial Account Object | ❌ | ❌ | ❌ | ✅ |
| Household Model | ❌ | ❌ | ❌ | ✅ |
| Einstein Activity Capture | ❌ | ❌ | ✅ | ✅ |
| Prompt Builder | ❌ | ❌ | ✅ | ✅ |
| Agentforce | ❌ | ❌ | Add-on | Add-on |

**DLK likely has**: Enterprise or FSC Enterprise. Many RIAs this size use Salesforce with an overlay. Ask in Week 1 audit.

**Important**: Process Builder and Workflow Rules were **retired Dec 31, 2025**. All new automation must use Flow Builder.

## What Small RIAs Underutilize (Our Value Proposition)

Most RIAs use Salesforce as a glorified Rolodex. **The gap between what they pay for and what they use is 60–70%.** This is the core value proposition for Advisor Intelligence.

| Feature | What It Does | % of RIAs Using It |
|---------|-------------|-------------------|
| **Action Plan Templates** | Auto-create task checklists on record creation | Very low |
| **Flow Automations** (Record-Triggered, Scheduled) | Automated business logic without code | Low |
| **Einstein Activity Capture** | Auto-logs emails and calendar events to CRM | Medium |
| **Custom Reports & Dashboards** | Business intelligence and pipeline visibility | Low |
| **Pipeline Management** | Track prospects through stages | Low-medium |
| **Prompt Builder Templates** | AI-powered field generation and summarization | Almost none |
| **Lightning Homepage Components** | Customized dashboard views per user | Low |
| **Schwab Advisor Center Integration** | Daily account data sync (free AppExchange app) | Medium |

## Schwab Advisor Center Integration

Available on AppExchange (free app). Capabilities:
- Daily data download (account details, balances, positions, alerts)
- Account opening from Salesforce
- SSO to Schwab from within Salesforce
- Uses Schwab OpenView Gateway (Performance Technologies, Inc.)
- Requires active Schwab custody relationship
- **Daily batch sync** (not real-time)

## Third-Party Overlays for RIAs

| Platform | Best For | Notes |
|----------|----------|-------|
| **Practifi** | Growing multi-advisor firms | Robust workflows, compliance tracking, eMoney integration |
| **XLR8 (Concenter)** | Solo to mid-size | Lower complexity, good without dedicated SF admin |
| **Salentica Elements** | Enterprise RIAs | Deep customization, 10+ users |

## What We Need for DLK Workflows

| Capability | Required For | Minimum Edition |
|-----------|-------------|-----------------|
| Record-Triggered Flow | WF2 (onboarding tasks) | Professional |
| Scheduled Flow | WF3 (review cycle triggers) | Professional |
| Custom Fields | WF2 + WF3 (review dates, status fields) | All editions |
| Lightning Homepage | WF2 + WF3 (pipeline dashboard) | All editions |
| Email Templates | WF3 (review request emails) | All editions |
| Task Auto-Creation | WF2 (onboarding checklist) | Professional (via Flow) |
| Reports/Dashboards | Both (pipeline and review visibility) | Professional |
| API Access | n8n webhook integration | Enterprise |

**Bottom line**: We need at minimum Professional edition. Enterprise is better (API access for n8n integration).

## Salesforce + AI Integration Paths

| Approach | Complexity | Cost | Best For |
|----------|-----------|------|----------|
| **Prompt Builder with external LLM calls** | Medium | Low | Cleanest native approach |
| **n8n middleware on VPS catching webhooks** | Medium | Low | Most flexible (our preferred) |
| **Third-party tools (Jump/Hazel) with native SF integration** | Low | Medium | Fastest to deploy |
| **Native Agentforce** | High | Very High | Enterprise-only |

## Flow Patterns for RIAs

- [[15-SALESFORCE/Flow-Patterns/Record-Triggered-Onboarding|Record-Triggered Onboarding]] — WF2 pattern
- [[15-SALESFORCE/Flow-Patterns/Time-Based-Review-Cycle|Time-Based Review Cycle]] — WF3 pattern
- [[15-SALESFORCE/Flow-Patterns/Task-Auto-Assignment|Task Auto-Assignment]] — Reusable pattern

## Common RIA Customizations

- Household object (group related contacts/accounts)
- Financial account tracking (AUM per account)
- Review date tracking and scheduling
- Pipeline stages for prospects
- Task templates for onboarding
- Integration with custodian (Schwab, Fidelity)
- Email template library for client communications

---

## Related

- [[00-ADVISOR-INTELLIGENCE/INDEX|Advisor Intelligence Hub]]
- [[20-CLIENTS/DLK/Tech-Stack/Salesforce-Audit|DLK Salesforce Audit]]
- [[10-INDUSTRY/Competitor-Tools/Agentforce|Agentforce]] — Salesforce's AI add-on
- [[10-INDUSTRY/Competitor-Tools/Jump|Jump]] — Third-party with SF integration
