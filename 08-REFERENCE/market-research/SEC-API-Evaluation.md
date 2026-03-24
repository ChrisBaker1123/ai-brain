---
type: reference
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
tags:
  - data-source
  - sec-edgar
  - api
  - dlk-prospecting
---

# SEC-API.io Evaluation

Last Updated: 2026-03-24

## Overview

sec-api.io is a commercial API service providing structured access to the entire SEC EDGAR filings corpus, dating back to 1993. It covers 20+ million filings and 100+ million exhibits, with new filings indexed within 300ms of EDGAR publication. Relevant to [[DLK-HUB]] prospecting work and the broader [[Business-Model]] for sourcing RIA prospect data.

## Pricing Tiers

| Tier | Price | Key Limits |
|------|-------|------------|
| **Free Trial** | $0 | 100 API calls total (not monthly — trial credits) |
| **Personal & Startups** | $55/mo | Standard rate limits, 5 GB data/mo |
| **Business** | $239/mo | Higher throughput, 15 GB data/mo, $0.30/GB overage |
| **Enterprise** | Custom | Multi-key access, redistribution rights, dedicated support |

Academic/research discounts available for professors, PhD researchers, and early-stage startups building MVPs.

## Key APIs and Features

### RIA/Advisor-Specific
- **Form ADV API** — Query all ADV filings by AUM, CRD number, state, services offered, number of clients, and more
- **Schedule A, B, D endpoints** — Access direct/indirect owners, financial industry affiliations, private fund data
- **Brochure endpoint** — Part 2 brochure data for any advisor
- Can query by Item 5G (advisory service types), Item 5H (financial planning client counts), AUM thresholds

### General
- **Query API** — Search/filter all 20M+ filings by CIK, ticker, company name, form type, date
- **Stream API** — Real-time WebSocket feed of new filings
- **Full-Text Search API** — Search full text of all filings since 2001
- **Extractor API** — Extract specific sections from 10-K/10-Q/8-K filings
- **XBRL-to-JSON converter** — Standardized financial statement extraction
- **Download API** — Up to 40 requests/second (vs EDGAR's 10 req/s limit)
- **13F Holdings API** — Institutional ownership monitoring
- **Executive Compensation API**
- **Insider Trading API**
- **Form D Offerings API**

## Comparison: sec-api.io vs Raw IAPD/EDGAR

| Factor | sec-api.io | Raw IAPD (data.gov) / EDGAR |
|--------|------------|------------------------------|
| **Cost** | $55-$239+/mo | Free |
| **Rate Limits** | Up to 40 req/s (paid) | 10 req/s (IP blocked for 10 min if exceeded) |
| **Data Format** | Clean JSON | Raw XML/SGML, needs parsing |
| **ADV Data** | Queryable API with structured fields | Bulk CSV/XML download, manual processing |
| **Real-time** | 300ms after EDGAR publication | Manual polling required |
| **Full-text search** | Yes (2001-present) | No (must download and index yourself) |
| **XBRL parsing** | Built-in JSON conversion | Manual XBRL/XML parsing |
| **Setup time** | Minutes (API key) | Days/weeks (build pipeline) |
| **Pagination** | Max 10,000 records per query | Download entire bulk files |

### Honest Assessment for Our Use Case
For [[DLK-HUB]] M&A prospecting, the raw IAPD bulk download from SEC.gov is **sufficient and free**. The current Python pipeline at `~/advisor-intelligence/dlk-prospecting/` already handles the bulk CSV data. sec-api.io would be valuable if we need:
- Real-time monitoring of new ADV filings (new RIA registrations)
- Structured queries across ADV fields without building our own parser
- Full-text search across filings

The $55/mo Personal tier would be adequate for periodic prospecting queries. The free trial (100 calls) is enough to evaluate the Form ADV API quality.

## Competitors

| Provider | Pricing | Notes |
|----------|---------|-------|
| **SEC EDGAR (direct)** | Free | 10 req/s, raw data, requires parsing |
| **SEC Filing Data (secfilingdata.com)** | Varies by tier | Education/research focus, JSON + downloadable formats |
| **Financial Modeling Prep (FMP)** | $14-$75/mo | Financial statements focus, not ADV-specific |
| **datajockey.io** | Free (beta) | Newer, processing SEC filings into user-friendly format |
| **SEC EDGAR MCP Server** | Free (open source) | AI-native access via MCP protocol, uses raw SEC API |
| **sec-edgar-api (Python)** | Free (wrapper) | Python wrapper for free SEC data.gov APIs |

## Rate Limiting Details

- Free SEC EDGAR: 10 requests/second, IP blocked 10 min if exceeded
- sec-api.io Free Trial: 100 total API calls
- sec-api.io Paid: Up to 60,000 filings within a 5-minute window (higher tiers)
- sec-api.io Download API: 40 requests/second

## Recommendation

**For now**: Continue using the free IAPD bulk download for DLK prospecting. The data is adequate and the pipeline works.

**Consider sec-api.io ($55/mo) when**: We need to offer real-time RIA monitoring as a consulting deliverable, or when manual parsing of ADV data becomes a bottleneck with multiple clients.

**Alternative worth exploring**: The SEC EDGAR MCP Server (open source) could provide conversational access to SEC data through Claude, which aligns with our AI consulting positioning.

## Needs Further Investigation
- Exact Form ADV field coverage vs what we get from IAPD bulk download
- Whether the $55/mo tier's rate limits are sufficient for batch prospecting
- Quality comparison: sec-api.io parsed ADV data vs our current IAPD pipeline output

## Sources
- https://sec-api.io/pricing
- https://sec-api.io/docs/investment-adviser-and-adv-api
- https://sec-api.io/docs
- https://github.com/janlukasschroeder/sec-api
- https://www.sec.gov/search-filings/edgar-application-programming-interfaces
- https://adviserinfo.sec.gov/adv
- https://www.findmymoat.com/tools/sec-api-sec-api-io
- https://www.reddit.com/r/algotrading/comments/13i8o9s/

## Related Notes
- [[DLK-HUB]]
- [[Business-Model]]
- [[Tech-Stack]]
- [[Competitive-Landscape]]
