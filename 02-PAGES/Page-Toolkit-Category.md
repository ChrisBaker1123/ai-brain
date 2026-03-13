# Page: Toolkit Category

#page #dashboard #templates

## Route
`/toolkit/[category]` — Protected (dynamic route)

## Purpose
View templates filtered to a specific category. Redirects to `/toolkit` with the category tab active.

## Layout
[[Component-Dashboard-Shell]]

## Implementation
46 lines — simply redirects to `/toolkit` with the category slug as a query parameter to activate the correct tab.

## URL Examples
- `/toolkit/estate-planning` → `/toolkit?tab=estate_planning`
- `/toolkit/deep-analysis` → `/toolkit?tab=deep_analysis`

## Related Notes
- [[Page-Toolkit]] — Parent page
- [[Architecture]] — URL slug conventions
