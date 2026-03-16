# Page: Document Builder

#page #dashboard #documents

## Route
`/documents` — Protected

## Purpose
Browse and use 20 document templates across 6 categories for multi-page client-facing documents.

## Layout
[[Component-Dashboard-Shell]]

## Content (233 lines)
- Category grid (6 categories)
- Document cards within each category
- Click → opens [[Component-Document-Runner]] modal

## Categories (6)
| Category | Templates |
|----------|-----------|
| comprehensive_plans | Financial plan summaries |
| market_analyses | Market analysis reports |
| performance_reviews | Portfolio review reports |
| client_education | Client education materials |
| regulatory_updates | Regulatory update docs |
| ad_hoc_documents | Misc professional documents |

## Supabase Dependencies
None — documents are client-side from `lib/documents-data.json`

## Related Notes
- [[Component-Document-Runner]] — Document modal
- [[Page-Documents-Category]] — Category view
