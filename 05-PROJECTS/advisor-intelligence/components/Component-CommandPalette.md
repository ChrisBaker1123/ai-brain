# Component: Command Palette

#component #feature

## File Path
`src/components/command-palette.tsx` (483 lines)

## Purpose
Cmd+K / Ctrl+K keyboard-activated search across all content.

## Search Index
`buildSearchIndex()` indexes: PROMPTS (61), DOCUMENTS (20), TUTORIALS (18), USE_CASES, PAGES

## Matching
`scoreResult()` — fuzzy matching on title, category, description, tags

## UI
- Fixed overlay at z-[100]
- Grouped results by type (MAX_PER_SECTION = 2)
- Keyboard nav: ArrowDown, ArrowUp, Enter, Escape
- Type badges with custom colors per content type
- Page icons mapping for navigation pages

## Used On
- [[Component-Dashboard-Shell]] — Always present in dashboard

## Related Notes
- [[Page-Toolkit]] — ⌘K hint shown in search bar
