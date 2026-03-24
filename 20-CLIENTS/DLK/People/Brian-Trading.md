---
type: contact
title: "Brian Johnson — DLK Trading"
status: active
created: 2026-03-24
updated: 2026-03-24
client: DLK
---

# Brian S. Johnson — Portfolio Management & Research

> Trading and rebalancing. Receives instructions from Mark. Needs cleaner handoff.

## Profile

| Field | Value |
|-------|-------|
| **Title** | Portfolio Management & Research |
| **Experience** | 17+ years |
| **Education** | B.A., Cal State San Bernardino |
| **Email** | bjohnson@dlkinvest.com |
| **LinkedIn** | [linkedin.com/in/brian-johnson](https://www.linkedin.com/in/brian-johnson-7530508a/) |

## What He Wants from AI

### Primary: Cleaner Rebalancing Handoff (WF4 — Future Workflow)

From transcript (Mark's description of the current workflow):

**Current process** (manual, inefficient):
1. Mark checks intelliflo redblack drift report each morning
2. Identifies accounts >5% off target allocation
3. Sends list to Brian (likely email or verbal): "Rebalance this account, this account, free up cash for this one"
4. Brian interprets the list, executes trades in Schwab Advisor Center
5. Risk of miscommunication or missed trades

**Desired workflow** (structured, automated):
- Mark's morning routine outputs a **structured rebalancing list** with:
  - Account name / ID
  - Current allocation vs target
  - Specific instructions: "Sell $X of position A, buy $Y of position B"
  - Cash flow needs: "Free up $10K for T. Rowe for new deposit"
  - Trading deadline (same day, or by EOW?)
- Brian receives this as **formatted task/email**, not ad-hoc message
- Brian confirms trades in Schwab, marks task complete
- System logs all trades (audit trail)

**Why it matters**: Reduces manual interpretation, improves execution speed, creates compliance documentation.

### Secondary: New Client Account Setup (WF2)

When a new client comes on, Brian needs:
- **Investment model assignment**: Which model does this client get? (Growth, Conservative, etc.)
- **Account setup in redblack**: Brian enters account data and assigns to model
- **Asset class allocation**: Based on model, what's the target allocation for this client?

**Workflow**: Part of [[20-CLIENTS/DLK/Workflows/WF2-Client-Onboarding/Spec|WF2]] — when Mark creates a new prospect in Salesforce:
- Auto-task created: "Brian: Set up account in redblack, assign model [MODEL_NAME]"
- Mark provides model choice in Salesforce (from dropdown or data)
- Brian sees task on homepage, completes it
- Task links to account in redblack so future drift reports automatically include the account

## Role at DLK

- Executes all trades in Schwab Advisor Center
- Fixed income specialist
- Conducts equity research with [[20-CLIENTS/DLK/People/Ted-Research|Ted Kay]]
- Receives rebalancing instructions from Mark and [[20-CLIENTS/DLK/People/Tom-CFP|Tom Brenner]]
- Sets up new client accounts in trading systems

## How to Work with Brian

- **Be specific**: Every trade instruction must be unambiguous (ticker, quantity, price limits if any)
- **Respect timing**: If rebalancing is due same-day, make that clear
- **Provide context**: Why is this rebalancing happening? (drift, new deposit, life event?) helps Brian understand priority
- **Compliance first**: Every trade should have audit trail for SEC review
- **Batch similar trades**: Group by account or ticker where possible to reduce execution risk

---

## Related

- [[DLK-HUB]] — Client hub
- [[20-CLIENTS/DLK/People/Team-Map|Team Map]]
- [[20-CLIENTS/DLK/Workflows/WF2-Client-Onboarding/Spec|WF2]] — His onboarding tasks
- [[20-CLIENTS/DLK/Workflows/WF-Backlog|WF-Backlog]] — Rebalancing handoff specs
- [[20-CLIENTS/DLK/People/Ted-Research|Ted Kay]] — Works with Brian on research/trading
- [[20-CLIENTS/DLK/People/Mark-Halby|Mark Halby]] — Sends Brian rebalancing instructions
