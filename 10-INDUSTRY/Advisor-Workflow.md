---
type: reference
title: "How Financial Advisors Spend Their Time"
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
---

# How Financial Advisors Spend Their Time

> Last Updated: 2026-03-24. Sources: Kitces Research, DLK transcript, industry benchmarks.

## Time Allocation

Advisors work 43–53 hours/week (average 48.7 hours per Kitces).

| Activity | % of Time | Hours/Week | Notes |
|----------|----------|-----------|-------|
| Client meetings | ~20% | ~8.5 hrs | Only 20% in actual meetings (Kitces) |
| Meeting prep and client servicing | ~34% | ~16.5 hrs | Largest single block |
| Business development | ~17% | ~8 hrs | Prospecting, networking |
| Investment management | ~10% | ~5 hrs | Portfolio review, rebalancing oversight |
| Administration | ~10% | ~5 hrs | Paperwork, operations |
| Compliance | ~8% | ~4 hrs | Documentation, reviews |
| Email/communication | ~included above | — | Spread across prep and admin |

**AI opportunity**: 50%+ of time is automatable (admin + prep + compliance + email)

## Per-Meeting Overhead

Each 1-hour client meeting has 1.5–2.5 hours of surrounding work:

| Task | Time | AI Potential |
|------|------|-------------|
| Pre-meeting prep (review CRM, compile notes, build agenda) | 20–30 min | AI meeting brief: 2–3 min |
| The meeting itself | 45–60 min | Recording + transcription |
| Post-meeting notes / CRM update | 30–60 min | AI summary: 5–10 min |
| Follow-up email | 15–20 min | AI draft: 2–3 min |
| CRM data entry | 15–20 min | Auto-populated from notes |
| Compliance documentation | 10–15 min | Auto-generated from transcript |
| **Total overhead** | **90–150 min** | **Compressible to 15–25 min** |

**Annual impact**: 520 hours/year on notes and CRM per advisor = $78,000–$208,000 in lost productivity

## Typical Day (from [[DLK-HUB|DLK]] — Mark Halby)

1. **Log into Schwab Advisor Center** — check alerts, maintenance items
2. **Log into intelliflo redblack** — check drift report (accounts >5% off target)
3. **Send rebalancing instructions to Brian** — "rebalance this account, free up cash for this one"
4. **Log into Salesforce** — enter data for new accounts, check homepage for upcoming reviews
5. **Review emails** — manage client requests (cash transfers, beneficiary updates, address changes)
6. **Send review scheduling emails** — manually email each client due for 90-day review
7. **Client meetings** — in-person or phone, periodic reviews and planning
8. **Follow-up** — meeting notes, action items, recap emails

## Where AI Saves Time (DLK Workflows)

| Activity | Current | With AI | Time Saved |
|----------|---------|---------|-----------|
| Onboarding tasks | Manual creation per client | Auto-generated on creation ([[20-CLIENTS/DLK/Workflows/WF2-Client-Onboarding/Spec\|WF2]]) | 30–45 min/client |
| Review scheduling | Individual emails per client | Auto-draft at 60 days ([[20-CLIENTS/DLK/Workflows/WF3-Review-Cycle/Spec\|WF3]]) | 15 min/client |
| Pre-meeting prep | Manual CRM review, note compilation | One-page auto-brief | 20 min/meeting |
| Post-meeting | Manual notes, task creation, recap email | AI-assisted structured update | 30 min/meeting |
| Prospecting research | Manual SEC searches | Automated weekly report ([[20-CLIENTS/DLK/Workflows/WF1-Advisor-Prospecting/Spec\|WF1]]) | 5+ hours/week |
| Fee audit | Manual contract-to-billing comparison | Automated quarterly check | 10+ hours/quarter |
| Morning routine | Login to 3 systems, check alerts | Consolidated dashboard | 30 min/day |

## Industry Benchmarks

- Top-performing advisors delegate more → spend 60%+ time with clients
- AI's biggest impact: shifting the ratio toward client-facing time
- AI tools claim to compress post-meeting from 60–90 min to 5–10 min
- Time value: $200–$400/hour for advisors, $40–$75/hour for staff

## What Each DLK Person Needs (from transcript)

| Person | Role | Primary Need |
|--------|------|-------------|
| **Don Dempster** | CEO/CCO | M&A prospecting, compliance automation (fee audit), CPA outreach |
| **Mark Halby** | CFP | Salesforce automation, virtual assistant, morning routine, meeting notes |
| **Ted Kay** | Research | Portfolio news monitoring, stock alerts on held names |
| **Brian Johnson** | Trading | Cleaner rebalancing handoff from Mark |
| **Tom Brenner** | CFP | Same as Mark (review cycle, onboarding) |

---

## Related

- [[RIA-Economics]] — Industry financial data
- [[AI-Adoption-Data]] — AI usage statistics
- [[DLK-HUB]] — Mark Halby's workflow from transcript
- [[15-SALESFORCE/FSC-Features|Salesforce Features]] — CRM automation capabilities
