---
type: reference
title: "DLK Workflow Backlog"
status: active
created: 2026-03-24
updated: 2026-03-24
client: DLK
---

# DLK Workflow Backlog

> Prioritized list of future workflows. Review monthly with Don and Mark.

## Priority Ranking

| # | Workflow | Owner | Category | Impact | Feasibility | Notes |
|---|---------|-------|----------|--------|-------------|-------|
| 1 | **WF1: M&A Prospecting Intelligence** | [[20-CLIENTS/DLK/People/Don-Dempster\|Don]] | Strategy | High | Medium | SEC IAPD → RIA filtering → LinkedIn → network intelligence. Don's #1 priority. 10–20 targets/week, ranked by connection. |
| 2 | **WF2: New Client Onboarding** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] | Operations | High | High | Auto-task list on prospect creation (disclosures, billing, model assignment, newsletter, calendar). Dashboard shows progress. |
| 3 | **WF3: Review Cycle Automation** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] + [[20-CLIENTS/DLK/People/Tom-CFP\|Tom]] | Operations | High | Medium | Track review dates. 60-day email, 30-day escalation, pre-meeting brief, post-meeting notes→CRM. Both CFPs use this. |
| 4 | **Fee Audit Automation** | [[20-CLIENTS/DLK/People/Don-Dempster\|Don]] | Compliance | High | Medium | Download client list from billing → cross-reference contracts → verify actual fees vs contracted. Quarterly report. Details below. |
| 5 | **Portfolio News Monitoring** | [[20-CLIENTS/DLK/People/Ted-Research\|Ted]] | Research | High | High | Daily 8 AM email with stock alerts (89 positions), material events, affected clients. High signal, low noise. |
| 6 | **Morning Routine Optimization** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] + [[20-CLIENTS/DLK/People/Tom-CFP\|Tom]] | Operations | Medium | Low | Consolidate Schwab alerts + redblack drift + CRM into single daily briefing. Requires multiple integrations. |
| 7 | **Rebalancing Handoff** | [[20-CLIENTS/DLK/People/Brian-Trading\|Brian]] | Trading | Medium | Medium | Structured Mark → Brian trade instructions (account, % drift, specific trades, cash needs). Audit trail. |
| 8 | **CPA Outreach Campaign** | [[20-CLIENTS/DLK/People/Don-Dempster\|Don]] | Marketing | Medium | High | Identify CPAs → 3-touch email sequence → task assignments for follow-up calls. Details below. |
| 9 | **Client Life Events** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] | Client Service | Medium | Medium | Track birthdays, graduations, milestones. Trigger personalized outreach. Don: "How many clients have kids graduating?" |
| 10 | **Client Request Triage** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] | Operations | Medium | Low | Inbox management: categorize (cash transfer, beneficiary, address change), prioritize, draft response. Needs M365 + Salesforce bridge. |
| 11 | **Post-Meeting Notes Pipeline** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] | Operations | Medium | High | In-person recording → transcription → structured CRM update. Dependent on WF3 and recording tool choice. |
| 12 | **Milestone Mailers** | [[20-CLIENTS/DLK/People/Mark-Halby\|Mark]] | Client Service | Low | High | Query CRM for clients with kids graduating → send personalized gift/card/swag. Don: "Send them a freaking Santa Cruz t-shirt." |

## Detailed Specs

### WF4: Fee Audit Automation (Don Dempster)

**The problem**: DLK is "highly, highly regulated." If the SEC audits and finds a client was charged a different fee than contracted, it's a violation. Manual reconciliation is error-prone.

**The process** (from transcript):
1. Download client list with fees from DLK's billing system
2. Cross-reference each client against signed advisory agreements (contracts)
3. For each client, verify:
   - **Contracted fee**: What fee schedule did they sign?
   - **Actual fee charged**: What's being billed in the billing system?
   - **Variance**: Does contracted match actual? If not, flag it.
   - **Non-billable assets**: Are there assets under advisement that DLK doesn't actively manage? (inherited stock, concentrated positions held for tax reasons)
   - **Reconciliation**: Account for non-billable assets when comparing fees
4. Generate quarterly report showing:
   - All clients, their contracted fee, actual fee billed, any variance
   - Accounts that are over-billed or under-billed (with amounts)
   - Non-billable asset reconciliation summary
   - Signed statement that audit is complete
5. Email report to Don quarterly (Jan 1, Apr 1, Jul 1, Oct 1)

**Delivery format**:
- Excel or PDF showing:
  - Client Name | CRD if applicable | Contracted Fee (%) | Assets Under Management | Billable Assets | Non-Billable Assets | Fee Charged | Variance | Notes
- Summary: "All clients audited. X clients match perfectly. Y clients flagged for review. Z discrepancies resolved."
- Signed by Cri with date

**Why this matters**: Don's background is SEC compliance. This is audit-ready documentation that protects DLK from regulatory risk.

### WF7: CPA Outreach Campaign (Don Dempster)

**The vision**: CPAs refer their clients to DLK for wealth management. "CPAs know your balance sheet. CPAs know you have cash. But we manage the money."

**The process**:
1. **Identify CPAs** in Southern California:
   - Firms with $100M+ in client AUM they manage or know about
   - Filter for practices that serve high-net-worth individuals (not small tax shops)
   - Focus on geographic proximity to DLK (Solana Beach area + broader San Diego County)
2. **Email sequence** (3 touches, 14 days apart):
   - **Email 1** (Day 0): Intro email — "We're a local RIA, we invest in individual securities, we work with clients like yours. Let's grab coffee."
   - **Email 2** (Day 14): Follow-up — "Wanted to check in and see if you got my last email. Here's a case study of a CPA relationship."
   - **Email 3** (Day 28): Final touch — "One more quick note before I move on..." — offer discovery call or send asset class performance overview
3. **CRM tasks**: Create Salesforce tasks for Don to personally call top 10 CPAs (highest fit) after email sequence starts
4. **Tracking**: Log response rates, meetings scheduled, partnerships formed

**Delivery**:
- List of 20–30 CPAs (name, firm, email, phone, brief note on why they're a fit)
- Email templates (pre-written, Don reviews and customizes)
- Salesforce tasks auto-created for Don's follow-up calls
- Weekly report: # of emails sent, # opened, # replies, # calls scheduled

**Why it matters**: CPAs are a warm channel for referrals. Don sees this as strategic GTM.

## Workflow Ideas (Unscoped)

- Compliance calendar automation (filing deadlines, review dates)
- Client portfolio performance reporting (monthly/quarterly performance vs benchmark)
- Prospect follow-up drip sequences (Salesforce automation for leads)
- Annual ADV update preparation (regulatory checklist)
- Client tax-loss harvesting alerts (seasonal workflow)
- Estate plan review triggers (every 3 years or after life events)
- Client education email library (quarterly tips sent to segments)

## Scoring Method

- **Impact**: How much time/money/risk does this save? (High/Medium/Low)
- **Feasibility**: Can we build it with current tools and access? (High/Medium/Low)
- **Client excitement**: How excited is the owner about this? (inferred from transcript)

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Engagement/Timeline|Timeline]]
- [[20-CLIENTS/DLK/People/Don-Dempster|Don Dempster]]
- [[20-CLIENTS/DLK/People/Mark-Halby|Mark Halby]]
- [[20-CLIENTS/DLK/People/Ted-Research|Ted Kay]]
- [[20-CLIENTS/DLK/People/Brian-Trading|Brian Johnson]]
