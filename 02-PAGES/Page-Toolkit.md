# Page: Toolkit (Template Library)

#page #dashboard #templates

## Route
`/toolkit` — Protected

## Purpose
Browse, search, and use all 61 templates across 11 categories.

## Layout
[[Component-Dashboard-Shell]]

## Content (315 lines)
- Search bar with ⌘K hint
- Category tabs (11 categories)
- Recently used categories from localStorage
- Grid of template cards showing:
  - Title, description
  - Time saved, difficulty badge
  - Up to 3 tag pills
  - Favorite star toggle (Supabase persistence)
  - Click → opens [[Component-Prompt-Runner]] modal

## Categories (11)
| Category ID | Display Name | Template Count |
|-------------|-------------|----------------|
| estate_planning | Estate Planning | 8 |
| client_communication | Client Emails | 6 |
| prospecting | Business Development | 6 |
| practice_management | Practice Management | 6 |
| client_education | Client Education | 6 |
| onboarding | Onboarding | 6 |
| life_events | Life Events | 5 |
| tax_planning | Tax Planning | 6 |
| retirement_planning | Retirement Planning | 6 |
| marketing_content | Marketing | 6 |
| deep_analysis | Deep Analysis | 8 |

## URL Convention
Category IDs use underscores in data → hyphens in URLs via `toSlug()`:
- Data: `estate_planning`
- URL: `/toolkit/estate-planning`

## Supabase Dependencies
- SELECT from `generation_outputs` (favorites status)
- INSERT to `generation_outputs` (on template copy)

## Related Notes
- [[Page-Toolkit-Category]] — Category-specific view
- [[Component-Prompt-Runner]] — Template modal
- [[Architecture]] — Category ID convention
