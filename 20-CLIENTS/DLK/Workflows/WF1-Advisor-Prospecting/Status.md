---
type: status
title: "WF1 Status"
status: building
created: 2026-03-24
client: DLK
---

# WF1: Advisor Prospecting — Status

| Field | Value |
|-------|-------|
| **Status** | Building — Phase 1 (Data Pipeline) |
| **Owner** | Don Dempster |
| **Builder** | Cri |
| **Started** | 2026-03-24 |
| **First deliverable ETA** | Week 3 (Apr 7-11) |

## Progress

- [x] Spec written
- [x] SEC IAPD data access researched (3 sources: IAPD API, EDGAR EFTS, sec-api.io)
- [x] Architecture documented
- [x] Pipeline scripts built (fetch → filter → report)
- [x] Filter criteria implemented (AUM, geography, ownership, investment type, age proxy)
- [x] Report generation working (markdown format, auto-saves to vault)
- [x] Sample pipeline tested successfully (10 sample firms → scored → report generated)
- [ ] Live SEC data download (IAPD API rate-limited, testing alternatives)
- [ ] Principal extraction from Schedule A data
- [ ] Cross-referencing layer built (LinkedIn/associations)
- [ ] First real report delivered to Don
- [ ] Cron job set up on VPS

## Blockers

- None currently — this workflow uses only public data, no DLK system access required

---

## Related

- [[20-CLIENTS/DLK/Workflows/WF1-Advisor-Prospecting/Spec|Spec]]
- [[DLK-HUB]]
