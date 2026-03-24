---
type: reference
title: "Salesforce Financial Services Cloud Features"
status: active
created: 2026-03-24
---

# Salesforce for RIAs — Feature Reference

> Populated with research findings. Updated as we learn more from DLK's actual edition.

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
| Agentforce | ❌ | ❌ | Add-on | Add-on |

**DLK likely has**: Professional or Enterprise (most common for ~$400M AUM firms with ~11 employees)

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

**Bottom line**: We need at minimum Professional edition. Enterprise is better (API access, more Flows).

## Flow Patterns for RIAs

- [[15-SALESFORCE/Flow-Patterns/Record-Triggered-Onboarding|Record-Triggered Onboarding]] — WF2 pattern
- [[15-SALESFORCE/Flow-Patterns/Time-Based-Review-Cycle|Time-Based Review Cycle]] — WF3 pattern
- [[15-SALESFORCE/Flow-Patterns/Task-Auto-Assignment|Task Auto-Assignment]] — Reusable pattern

## Salesforce Pricing (approximate, 2026)

| Edition | Per User/Month | Annual (6 users) |
|---------|---------------|------------------|
| Essentials | $25 | $1,800 |
| Professional | $80 | $5,760 |
| Enterprise | $165 | $11,880 |
| FSC (Financial Services Cloud) | $300 | $21,600 |

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
