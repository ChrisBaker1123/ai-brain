---
type: document
title: "DLK Tool Recommendations"
status: draft
created: 2026-03-24
client: DLK
---

# DLK Tool Recommendations

> Based on research and transcript analysis. Present to Don and Mark during Week 1.

## Recommended Additions

### 1. Meeting Transcription: Zocks ($67-184/mo per seat)

**Why Zocks over competitors**: Zocks does NOT record audio — it only stores generated notes. This privacy-first architecture is ideal for Don's compliance culture. No audio files to archive or worry about.

| Feature | Zocks | Jump | Fathom |
|---------|-------|------|--------|
| In-person meetings | Mobile app | Mobile support | No |
| Records audio | **No** (privacy-first) | Yes | Yes |
| Salesforce integration | Yes | Yes | No |
| Post-meeting summary | Yes | Yes | Yes |
| Follow-up tasks | Yes | Yes | Limited |
| Compliance-friendly | **Best** | Good | OK |
| Price/seat/month | $67-$184 | Custom | $29 |

**Alternative**: Jump AI ($custom) — better "Ask Anything" feature for querying past meetings, but records audio.

**For DLK**: Recommend 2 seats (Mark + Tom) = $134-$368/month.

### 2. Schwab Advisor Center Integration (Free)

Already available on Salesforce AppExchange. Capabilities:
- Daily sync of account details, balances, positions, alerts into Salesforce
- SSO to Schwab from within Salesforce
- Account opening directly from Salesforce

**Impact**: Eliminates Mark's manual step of logging into Schwab separately each morning. Alerts appear directly in Salesforce.

### 3. Salesforce Overlay: Evaluate Practifi or XLR8

If DLK is running raw Salesforce without an overlay, a pre-built RIA overlay would dramatically reduce implementation time for our workflows.

| Overlay | Best For | Complexity |
|---------|----------|-----------|
| **Practifi** | Multi-advisor firms, compliance tracking | Higher (more features) |
| **XLR8** | Solo to mid-size, no dedicated SF admin | Lower (simpler) |

**Recommendation**: Evaluate during Salesforce audit. If they have no overlay, recommend XLR8 for simplicity.

## Already Using (Optimize)

### Microsoft 365 Copilot

Mark is already experimenting. Help him:
- Configure task recognition in email → Microsoft To Do
- Set up meeting summarization in Teams
- Connect To Do tasks with Salesforce (via Power Automate or Flow)

### Salesforce (Massive Optimization Opportunity)

"We know it does more than it is doing right now." Build Flows, dashboards, and automations. See WF2 and WF3 specs.

## Not Recommended (Yet)

| Tool | Why Not Yet |
|------|------------|
| **Hazel** (Altruist) | Only for Altruist clients. DLK custodies at Schwab. |
| **Agentforce** | $2/conversation or $125/user/month extra. Overkill for 6 advisors. Revisit in Month 3+ if Salesforce workflows prove value. |
| **FP Alpha** | Estate/tax document analysis. Not a current pain point for DLK. Revisit if workflow backlog prioritizes estate planning. |

## Cost Summary

| Tool | Monthly | Annual | Impact |
|------|---------|--------|--------|
| Zocks (2 seats) | $134-$368 | $1,608-$4,416 | Meeting transcription → CRM automation |
| Schwab SF Integration | Free | Free | Eliminates manual Schwab login |
| Salesforce Overlay (if needed) | TBD | TBD | Faster workflow implementation |
| **Total new costs** | **$134-$368** | **$1,608-$4,416** | |

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Tech-Stack/Current-Stack|Current Stack]]
- [[20-CLIENTS/DLK/Compliance/Vendor-Due-Diligence|Vendor Due Diligence]]
