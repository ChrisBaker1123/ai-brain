# Page: History

#page #dashboard

## Route
`/history` — Protected

## Layout
[[Component-Dashboard-Shell]]

## Content (70 lines)
- List of past outputs from `generation_outputs`
- Dynamic count in header
- Empty state when no history

## Supabase Dependencies
- SELECT from `generation_outputs` ORDER BY created_at DESC

## Related Notes
- [[Page-Favorites]] — Related feature
- [[Schema]] — generation_outputs table
