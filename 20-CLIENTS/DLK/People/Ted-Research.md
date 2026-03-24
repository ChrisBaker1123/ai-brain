---
type: contact
title: "Ted Kay — DLK Head of Research"
status: active
created: 2026-03-24
updated: 2026-03-24
client: DLK
---

# Theodore J. Kay — Managing Partner, Research

> Head of research and portfolio construction. Needs portfolio monitoring and stock alerts.

## Profile

| Field | Value |
|-------|-------|
| **Title** | Managing Partner, Portfolio Management & Research |
| **Credentials** | CFA (per some sources), Series 65 confirmed |
| **Education** | B.S. Finance & Entrepreneurship, U of Arizona |
| **CRD** | 5643664 |
| **Email** | tkay@dlkinvest.com |
| **LinkedIn** | [linkedin.com/in/theodorekay](https://www.linkedin.com/in/theodorekay) |

## What He Wants from AI

### Primary: Portfolio News Monitoring (WF4 — Future Workflow)

From transcript (Mark describing Ted's exact needs):
- **Daily news alerts on all stocks they hold** (89 positions per latest 13F)
- **Material events affecting portfolio names**: earnings surprises, management changes, regulatory actions, lawsuits, M&A rumors, industry disruption
- **Client intersection**: Cross-reference affected stock against which clients own it (allows proactive client outreach)
- **Client location intelligence**: "Is there a forest fire? Did a building burn down?" — geographic events affecting clients (real estate holdings, concentrated positions)
- **Daily intelligence brief** — email at 8 AM with priority-ranked items

**Example from transcript**: If Intel releases earnings that exceed expectations, the system flags that (1) DLK holds Intel, (2) 23 clients own Intel, (3) here's the earnings summary, (4) here's a template for calling clients with the news.

### System Requirements

**Data sources**:
- Stock tickers from DLK's 13F (89 positions)
- Client portfolio holdings (cross-reference which clients own each stock)
- Client location data (address, real estate concentration)
- News feeds: earnings calendars, SEC EDGAR filings, news aggregators (Yahoo Finance API, AlphaVantage, NewsAPI, SEC EDGAR)

**Filtering logic**:
- **High signal, low noise**: Only flag events that materially affect portfolio value or client wealth
- **Earnings surprises**: Beat/miss by >5%
- **Management changes**: C-suite departures, insider sales
- **Regulatory**: SEC investigation, lawsuit, delisting risk
- **Market events**: Stock splits, dividend changes, M&A rumors
- **Industry disruption**: New competitor, technology shift, commodity price changes

**Delivery format**: Daily 8 AM email to Ted
- **Today's material events** (sorted by impact on DLK portfolio)
  - Ticker | Event | Impact | Affected Clients (count)
  - Paragraph summary for each top-3 item
- **Week ahead**: Earnings coming for stocks Ted holds (calendar format)
- **Client action suggestions**: If event warrants client call, auto-suggest talking points

### Secondary: Research Tool Optimization

From transcript: Ted wants to optimize his research workflow but details aren't fully specified. Implied needs:
- Faster access to research on held names
- Integration of news/earnings into existing research process
- Ability to surface research insights to clients

## Role at DLK

- Oversight of all research and investment process
- Portfolio construction and risk management
- Co-founder (the "K" in DLK: Dempster-?-Kay)
- Works closely with [[20-CLIENTS/DLK/People/Brian-Trading|Brian Johnson]] on trading decisions
- Sets research standards for equity research with Brian

## How to Work with Ted

- **Deliver concise, data-driven intelligence** — He's a research professional; don't oversimplify
- **High signal, low noise** — Better to miss an event than deliver noise
- **Portfolio monitoring workflow should be automated** — He doesn't have time to manually scan news
- **Respect market hours** — 8 AM delivery is before market open; timing is critical
- **Data quality first** — If the system makes mistakes, he won't trust it; verify sources

---

## Related

- [[DLK-HUB]] — Client hub
- [[20-CLIENTS/DLK/People/Team-Map|Team Map]]
- [[20-CLIENTS/DLK/Workflows/WF-Backlog|Workflow Backlog]] — Portfolio monitoring is priority #4
- [[20-CLIENTS/DLK/People/Brian-Trading|Brian Johnson]] — Works with Ted on portfolio decisions
