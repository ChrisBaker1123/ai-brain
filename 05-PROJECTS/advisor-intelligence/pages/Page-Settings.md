---
type: reference
title: "Page: Settings"
status: active
created: 2026-03-13
updated: 2026-03-16
domain: product
---

# Page: Settings

#page #dashboard

## Route
`/settings` — Protected

## Layout
[[Component-Dashboard-Shell]]

## Content (42 lines)
Currently a stub — links to edit profile.

## Bug Fixed
Settings page previously saved `firstName` back to DB, destroying last names. Fixed to save `fullName`.

## Improvements Needed
- Full settings form (not a stub)
- Theme persistence, notification prefs, data export, account deletion

## Related Notes
- [[User-Model]] — Profile fields
- [[Page-Profile]] — Initial onboarding form
