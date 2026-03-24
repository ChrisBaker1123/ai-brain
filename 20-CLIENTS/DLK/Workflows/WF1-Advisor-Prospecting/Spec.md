---
type: spec
title: "WF1: Advisor Prospecting Intelligence System"
status: building
created: 2026-03-24
client: DLK
owner: Don Dempster
---

# WF1: Advisor Prospecting Intelligence System

> Don's #1 strategic priority. Identify independent RIAs for succession planning / M&A conversations.

## Problem

DLK wants to acquire or partner with aging advisors who invest in individual securities. Today, Don does this manually or through a partner. He wants a systematic, repeatable intelligence pipeline.

## Requirements (from transcript)

1. **Identify RIAs** matching criteria:
   - Invest in individual securities (not just mutual funds/ETFs)
   - Independently owned by individuals (not trusts, holding companies, PE-backed)
   - Geographic focus: Southern California first, then expand
   - AUM range: ~$100M–$500M (sweet spot for DLK's capabilities)
   - Principal age indicators where available (target 65-80)

2. **Scrub/filter**:
   - Remove firms owned by trusts or larger entities
   - Identify the actual person behind each firm (Schedule A / ownership data)
   - Remove firms already in DLK's existing network/CRM

3. **Cross-reference**:
   - Each principal → search LinkedIn for connections to DLK team
   - Shared board memberships, nonprofits, professional associations (FPA, CFA Society)
   - Shared geography, education, or career history

4. **Generate intelligence brief**:
   - For each target: name, firm, AUM, investment style, years in business
   - Age if available
   - Connections to DLK network
   - Suggested approach angle
   - Ranked by connection strength

5. **Delivery**:
   - Weekly email to Don
   - 10-20 targets per report
   - Store in vault for historical tracking
   - Ideally also import as Salesforce prospect records (future)

## Data Sources

### Primary: SEC IAPD / Form ADV
- **URL**: https://adviserinfo.sec.gov
- **Bulk data**: SEC provides monthly bulk data downloads of Form ADV filings
- **Key fields**:
  - Item 5: Types of advisory services and assets (identifies individual securities vs funds)
  - Schedule A: Direct/indirect owners and executive officers
  - Item 1: Firm name, CRD, address, AUM
  - Item 5.D: Approximate number of clients
  - Item 5.F: Discretionary AUM

### Secondary: SEC EDGAR 13F
- Firms with $100M+ in 13F securities file quarterly holdings
- Confirms individual stock investing style
- Available via EDGAR XBRL/XML feeds

### Tertiary: LinkedIn / Web
- Principal name → LinkedIn profile → connections analysis
- Firm website → about page → team bios, community involvement
- Professional association directories (FPA, CFA Institute, NAPFA)

## Technical Architecture

```
┌─────────────────────────┐
│  SEC IAPD Bulk Data     │ Monthly download (CSV/XML)
│  (Form ADV filings)     │
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│  Python: Parse & Filter │ Filter for individual securities,
│  (parse_adv.py)         │ individual ownership, geography, AUM
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│  Python: Scrub          │ Remove trusts/entities, identify principals,
│  (scrub_firms.py)       │ deduplicate, remove known firms
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│  Python: Cross-Ref      │ LinkedIn API / web search for each principal,
│  (cross_reference.py)   │ find connections to DLK team
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│  Python: Report Gen     │ Generate formatted intelligence brief,
│  (generate_report.py)   │ rank by connection strength
└──────────┬──────────────┘
           ▼
┌──────────┴──────────────┐
│  Delivery               │
├─────────────────────────┤
│  Email → Don            │ Weekly (cron)
│  Vault → Prospecting-   │ Archive all reports
│  Reports/               │
│  Salesforce → Prospects │ (future) Import as records
└─────────────────────────┘
```

## Infrastructure

| Component | Location |
|-----------|----------|
| Scripts | `~/dlk-prospecting/` on DigitalOcean VPS |
| Schedule | Weekly cron job (Monday 7 AM PT) |
| Data storage | VPS local + vault sync |
| Reports | `~/obsidian-vault/20-CLIENTS/DLK/Deliverables/Prospecting-Reports/` |

## MVP Scope (Week 1-3)

### Phase 1: Data Pipeline (Week 1)
- [ ] Download SEC IAPD bulk data
- [ ] Write parser for Form ADV data
- [ ] Filter by: individual securities investing, individual ownership, SoCal, AUM range
- [ ] Output: CSV of ~200-500 candidate firms

### Phase 2: Enrichment (Week 2)
- [ ] Extract principal names from Schedule A data
- [ ] Enrich with firm details (years in business, detailed investment style)
- [ ] Age estimation where possible (years since first registration)
- [ ] Remove firms already in DLK's network (manual list from Don)

### Phase 3: Intelligence (Week 3)
- [ ] Cross-reference principals against DLK team connections
- [ ] Generate ranked intelligence brief
- [ ] Email delivery system
- [ ] Deliver first report to Don for feedback

### Phase 4: Iteration (Month 2+)
- Refine filters based on Don's feedback
- Add LinkedIn connection analysis
- Add professional association data
- Salesforce import capability
- Expand geography beyond SoCal

## Open Questions

1. SEC IAPD: API vs bulk download? What's the best programmatic access?
2. LinkedIn: API limitations? Alternatives (Apollo.io, ZoomInfo)?
3. How does DLK define "invest in individual securities" precisely? (Item 5 checkbox?)
4. Does Don have an existing target list to exclude/include?
5. What's DLK's existing LinkedIn connection count? (for cross-referencing)

## Success Criteria

Don considers this successful if:
- He receives a weekly report with 10-20 viable targets
- Each target includes connection intel he can act on
- The approach angle is specific enough to write a personalized letter
- Targets are genuinely independent, individual-stock firms (not false positives)

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Workflows/WF1-Advisor-Prospecting/Architecture|Architecture]]
- [[20-CLIENTS/DLK/People/Don-Dempster|Don Dempster]]
