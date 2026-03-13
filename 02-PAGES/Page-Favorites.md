# Page: Favorites

#page #dashboard

## Route
`/favorites` — Protected

## Layout
[[Component-Dashboard-Shell]]

## Content (68 lines)
- Grid of favorited outputs from `generation_outputs`
- Dynamic count display
- Empty state message

## Supabase Dependencies
- SELECT from `generation_outputs` WHERE `is_favorited = true`

## Related Notes
- [[Schema]] — generation_outputs table, partial index on is_favorited
- [[API-Routes]] — POST /api/favorite toggle
- [[Page-History]] — Related feature
