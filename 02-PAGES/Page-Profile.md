# Page: Profile (Onboarding)

#page #onboard #auth

## Route
`/profile` — Protected (redirected here after signup)

## Purpose
Multi-step onboarding to collect advisor profile data for template personalization.

## Layout
Standalone (no dashboard shell, no marketing nav)

## Flow (604 lines)
### Screen 1: Professional Info
- Full name (text input)
- Firm type (button group: RIA, Wirehouse, IBD, Hybrid)
- AUM range (button group)
- Client specialties (multi-select)
- Pain points (multi-select)

### Screen 2: Communication Style
- Tone preference: formal, professional_warm, conversational
- Live preview card showing sample text in selected tone
- Each option has description text

### Confirmation Screen
- Summary of all selections
- "Start Using Templates" CTA
- Skip option available

## Supabase Dependencies
- INSERT/UPDATE on `advisor_profiles`
- Uses RLS-protected client

## Components Used
Button groups (not dropdown selects), multi-select with pipe delimiter

## Important Notes
- Multi-select delimiter is pipe `|` (not comma) to avoid collisions
- Inputs use button groups, NOT dropdown menus
- Redirects to `/subscribe` (paywall) or `/dashboard` after completion

## Related Notes
- [[Auth-Flow]] — Where this fits in signup flow
- [[User-Model]] — What data is collected and why
- [[Schema]] — advisor_profiles table
- [[Page-Dashboard]] — Destination after onboarding
