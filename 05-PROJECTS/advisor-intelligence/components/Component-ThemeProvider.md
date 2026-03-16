---
type: reference
title: "Component: Theme Provider"
status: active
created: 2026-03-13
updated: 2026-03-16
domain: product
---

# Component: Theme Provider

#component

## File Path
`src/components/theme-provider.tsx` (13 lines)

## Purpose
Wraps app with next-themes ThemeProvider.

## Config
- `attribute="class"` — Applies theme via CSS class
- `defaultTheme="light"` — Light mode by default
- `enableSystem` — Respects OS preference

## Used On
- Root layout (`app/layout.tsx`)

## Related Notes
- [[Design-System]] — Light/dark color system
