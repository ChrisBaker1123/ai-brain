# Page: Dashboard

#page #dashboard

## Route
`/dashboard` — Protected

## Purpose
Main landing page after login. Personalized action cards and quick access to features.

## Layout
[[Component-Dashboard-Shell]] (sidebar + header)

## Content (383 lines)
- Personalized welcome: "Welcome back, {firstName}" using `full_name.split(" ")[0]`
- 4 action cards based on user's `pain_points` profile field
- AI Coach as compact single-row link (blue gradient)
- No coaching banners, daily tips, or compliance warnings
- No usage counters or upgrade CTAs

## Action Card Personalization
Cards rendered conditionally based on `pain_points` array from profile. Each card links to relevant templates or features.

## Supabase Dependencies
- SELECT from `advisor_profiles` (user profile)
- Login tracking: POST to `/api/admin/track-login`

## Components Used
- [[Component-Dashboard-Shell]] — Layout wrapper
- [[Component-CommandPalette]] — Cmd+K search
- [[Component-SiteTour]] — Interactive tutorial
- [[Component-ChatWidget]] — Floating AI Coach

## Related Notes
- [[User-Model]] — pain_points drive card personalization
- [[Page-Toolkit]] — Template library
- [[Page-Chat]] — AI Coach full page
- [[Component-Dashboard-Shell]] — Layout details
