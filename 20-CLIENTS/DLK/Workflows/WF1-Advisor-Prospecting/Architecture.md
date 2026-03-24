---
type: architecture
title: "WF1: Advisor Prospecting — Technical Architecture"
status: active
created: 2026-03-24
client: DLK
---

# WF1: Advisor Prospecting — Technical Architecture

## System Overview

```
                    ┌──────────────┐
                    │  SEC IAPD    │ Monthly bulk data (CSV/XML)
                    │  Form ADV    │ adviserinfo.sec.gov/compilation
                    └──────┬───────┘
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
    ┌─────────────┐ ┌──────────┐ ┌───────────┐
    │ IAPD API    │ │ EDGAR    │ │ sec-api.io│
    │ (primary)   │ │ (backup) │ │ (enriched)│
    └──────┬──────┘ └────┬─────┘ └─────┬─────┘
           └──────────┬──┘             │
                      ▼                │
              ┌───────────────┐        │
              │ fetch_advisers│◄───────┘
              │ .py           │ CSV → data/
              └───────┬───────┘
                      ▼
              ┌───────────────┐
              │ filter_firms  │ Apply Don's criteria
              │ .py           │ Score and rank
              └───────┬───────┘
                      ▼
              ┌───────────────┐
              │ generate_     │ Markdown intelligence brief
              │ report.py     │ Weekly delivery
              └───────┬───────┘
                      │
           ┌──────────┼──────────┐
           ▼          ▼          ▼
    ┌──────────┐ ┌────────┐ ┌────────────┐
    │ Email    │ │ Vault  │ │ Salesforce │
    │ to Don   │ │ Report │ │ (future)   │
    └──────────┘ └────────┘ └────────────┘
```

## Data Sources — Research Findings

### 1. SEC IAPD Bulk Data (Primary)

**URL**: https://adviserinfo.sec.gov/compilation
**Format**: Monthly ZIP files containing spreadsheets
**Content**: All SEC-registered investment adviser firms
**Key fields**: CRD, legal name, AUM, state, registration date, SEC status
**Cost**: Free
**Update frequency**: Monthly
**Access**: Direct download (may require browser — anti-bot protections on API)

**Limitation**: Bulk data provides firm-level summary but NOT detailed Form ADV item-level data (investment types, Schedule A ownership). Need to query individual firms for detail.

### 2. IAPD REST API

**Base URL**: https://api.adviserinfo.sec.gov/IAPD/Content/Search/api/
**Endpoints**:
  - `/Firm?query=&stateCode=CA&pageSize=50&page=1` — Search firms
  - `/Firm/{crd}` — Individual firm detail
**Format**: JSON
**Cost**: Free
**Limitation**: Rate-limited, returns 403 on heavy use. Need respectful pagination with delays.

### 3. SEC EDGAR EFTS (Full-Text Search)

**URL**: https://efts.sec.gov/LATEST/search-index
**Format**: JSON (Elasticsearch)
**Content**: Full text of all EDGAR filings
**Cost**: Free, no API key
**Limitation**: Form ADV goes through IARD (not EDGAR). Limited ADV data in EDGAR.

### 4. sec-api.io (Enriched, Structured)

**URL**: https://sec-api.io
**Format**: JSON REST API
**Content**: Structured Form ADV data including all items and schedules
**Cost**: Free tier = 100 calls/month. Paid tiers from $25/month.
**Key advantage**: Provides structured access to Item 5 (investment types) and Schedule A (ownership) — exactly what Don needs for filtering.

### 5. SEC 13F Filings (Supplemental)

**URL**: https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&type=13F
**Content**: Quarterly holdings for firms with $100M+ in 13F securities
**Use case**: Confirms individual stock investing style (vs. mutual funds only)
**Python**: `sec-edgar-downloader` package can fetch 13F filings

## Recommended Approach

### Phase 1 (Now): Hybrid — IAPD bulk + API detail
1. Download monthly IAPD compilation data (bulk CSV)
2. Filter for CA, AUM range, SEC-registered
3. For top candidates, query IAPD API for Form ADV detail
4. Rate-limit API calls (2-second delays, max 200/day)

### Phase 2 (If API blocked): sec-api.io
1. Use sec-api.io free tier (100 calls/month) for structured ADV data
2. Query by state, AUM, investment type
3. Get Schedule A ownership data directly

### Phase 3 (Production): Firecrawl + sec-api.io
1. Use Firecrawl MCP to scrape IAPD search results at scale
2. Use sec-api.io for enrichment of top candidates
3. Cross-reference with 13F filings for investment style confirmation

## Infrastructure

| Component | Location | Details |
|-----------|----------|---------|
| **Scripts** | `~/advisor-intelligence/dlk-prospecting/` | Python pipeline |
| **Data** | `~/advisor-intelligence/dlk-prospecting/data/` | Raw CSV/JSON from SEC |
| **Output** | `~/advisor-intelligence/dlk-prospecting/output/` | Filtered, scored firms |
| **Reports** | Vault: `20-CLIENTS/DLK/Deliverables/Prospecting-Reports/` | Weekly reports for Don |
| **Schedule** | Cron on VPS (future) | Monday 7 AM PT weekly run |

## Pipeline Scripts

| Script | Purpose | Input | Output |
|--------|---------|-------|--------|
| `config.py` | Configuration (criteria, exclusions, DLK team) | — | — |
| `fetch_advisers.py` | Fetch raw adviser data from SEC sources | SEC APIs | `data/*.csv` |
| `scrape_iapd.py` | Alternative: scrape IAPD directly | IAPD website | `data/*.csv` |
| `filter_firms.py` | Apply Don's criteria, score and rank | `data/*.csv` | `output/scored_firms.csv` |
| `generate_report.py` | Create weekly intelligence brief | `output/scored_firms.csv` | `reports/report-YYYY-MM-DD.md` |
| `run_pipeline.py` | Orchestrate full pipeline | — | Full run |

## Cross-Referencing (Future Enhancement)

### LinkedIn Connection Analysis
**Challenge**: LinkedIn has strict API access and anti-scraping policies.
**Options**:
1. **Apollo.io** — Business intelligence platform, has LinkedIn data, API available (~$99/mo)
2. **ZoomInfo** — Contact and company database, expensive ($10K+/year)
3. **Manual** — Don provides his LinkedIn connection list, we match against principals
4. **RocketReach** — Email/LinkedIn lookup ($53/mo starter)

**Recommendation**: Start with manual matching (Don exports connections), add Apollo.io if volume justifies cost.

### Professional Association Cross-Reference
- FPA member directory: https://www.financialplanningassociation.org
- CFA Society San Diego: member directory
- NAPFA: https://www.napfa.org/find-an-advisor

## Testing

```bash
# Run with sample data
cd ~/advisor-intelligence/dlk-prospecting
python3 run_pipeline.py --sample

# Run live pipeline
python3 run_pipeline.py

# Just fetch data
python3 run_pipeline.py --fetch-only

# Just generate report from existing data
python3 run_pipeline.py --report-only
```

## Security Notes

- All data is publicly available SEC filings
- No DLK client data is used in this system
- No login credentials stored in code (API keys via environment variables)
- Reports contain only public information about target firms

---

## Related

- [[20-CLIENTS/DLK/Workflows/WF1-Advisor-Prospecting/Spec|WF1 Spec]]
- [[20-CLIENTS/DLK/Workflows/WF1-Advisor-Prospecting/Status|WF1 Status]]
- [[20-CLIENTS/DLK/People/Don-Dempster|Don Dempster]]
- [[DLK-HUB]]
