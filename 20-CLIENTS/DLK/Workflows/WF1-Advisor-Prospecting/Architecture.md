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

### 1. SEC Monthly IA Information Reports (Primary — Best Free Source)

**URL**: https://www.sec.gov/data-research/sec-markets-data/information-about-registered-investment-advisers-exempt-reporting-advisers
**Also**: https://catalog.data.gov/dataset/information-about-registered-investment-advisers-and-exempt-reporting-advisers
**Format**: Monthly ZIP containing XLSX/CSV spreadsheet
**Files**: `ia{MMYYYY}.zip` (registered advisers), `ia{MMYYYY}-exempt.zip` (exempt reporting)
**Content**: Full Form ADV Part 1 data for ALL SEC-registered firms
**Key fields**:
  - Item 1: Firm name, CRD, SEC file number, address, phone
  - Item 3: Form of organization (LLC, Corp, Partnership, Sole Proprietor)
  - Item 5.D: Client types with counts and RAUM per category
  - Item 5.F: Total AUM (discretionary, non-discretionary, total)
  - Item 5.G: Advisory activities (`Q5G2` = portfolio management for individuals)
  - Item 7A: Financial industry affiliations (no BD affiliation = independent)
  - Item 10: Control persons
**Cost**: Free (public domain)
**Update frequency**: Monthly

### 1b. SEC XML Compilation Feeds (Alternative Bulk Source)

**URL**: `https://reports.adviserinfo.sec.gov/reports/CompilationReports/IA_FIRM_SEC_Feed_{MM_DD_YYYY}.xml.gz`
**Also**: `IA_INDVL_Feed_{MM_DD_YYYY}.xml.zip` (individual advisers)
**Format**: Gzipped XML with complete Form ADV Part 1A data
**Content**: All SEC-registered firms, full ADV data structure
**Cost**: Free
**Individual ADV PDFs**: `https://reports.adviserinfo.sec.gov/reports/ADV/{CRD}/PDF/{CRD}.pdf`

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

### 4. sec-api.io (Enriched, Structured — Best Paid Option)

**URL**: https://sec-api.io
**Format**: JSON REST API (9 endpoints for Form ADV)
**Content**: Structured Form ADV data including all items and schedules
**Cost**: Free tier = 100 calls. Paid: $49/mo (Personal), $199/mo (Business).
**Database**: 41,000+ firm ADV filings, 380,000+ individual advisers, updated daily.
**Key endpoints**:
  - `POST /form-adv/firm` — Search by any ADV field (Lucene syntax)
  - `GET /form-adv/schedule-a-direct-owners/{crd}` — Direct owners and officers
  - `GET /form-adv/schedule-d-5-k/{crd}` — SMA asset categories (individual securities filter!)
**Critical fields for Don's criteria**:
  - **Item 5.K (Schedule D)**: SMA asset breakdown — `exchange-traded equity securities` and `non-exchange-traded equity securities` percentages identify individual stock managers
  - **Schedule A**: Owner name, title, ownership code, entity type (individual vs. corp/trust), control person flag
  - **Item 5.F**: `Q5F2C` = total RAUM (filterable: `Q5F2C:[150000000 TO 750000000]`)

### 5. SEC 13F Filings (Supplemental)

**URL**: https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&type=13F
**Content**: Quarterly holdings for firms with $100M+ in 13F securities
**Use case**: Confirms individual stock investing style (vs. mutual funds only)
**Python**: `sec-edgar-downloader` package can fetch 13F filings

## Recommended Approach

### Phase 1 (Now — $0): Monthly SEC spreadsheet + IAPD API
1. Download monthly IA Information Report from SEC data portal (`ia{MMYYYY}.zip`)
2. Load spreadsheet into pandas, filter on Item 3 (org type), Item 5.F (AUM), Item 5.G (portfolio mgmt), Item 7A (no BD affiliation), address (CA)
3. Extract CRD numbers for matching firms (~200-500 candidates)
4. For top 50-100, query undocumented IAPD API (`api.adviserinfo.sec.gov/search/firm`) for enrichment
5. Use respectful rate limiting (2-sec delay, User-Agent with contact email)

### Phase 2 (Week 2 — $0): Schedule A ownership + historical CSV
1. Download historical Schedule A CSV from SEC FOIA page (covers through Dec 2024)
2. Join on CRD to get direct owner names, entity types, control person flags
3. Filter: keep only firms where owner entity type = individual person
4. Extract principal names (control person = Y, or title = CEO/President/Managing Member)

### Phase 3 (Month 2 — $49/mo): sec-api.io for investment type + live Schedule A
1. Use sec-api.io Schedule D 5.K endpoint to get SMA asset category breakdowns
2. Filter for high % in "exchange-traded equity securities" = individual stock managers
3. Use live Schedule A endpoint for current ownership data
4. Cross-reference with 13F filings for confirmation

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
