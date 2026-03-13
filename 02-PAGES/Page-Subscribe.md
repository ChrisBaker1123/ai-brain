# Page: Subscribe (Paywall)

#page #onboard

## Route
`/subscribe` — Protected

## Purpose
Paywall between onboarding and dashboard. 5 lines — redirects to Stripe checkout.

## Flow
After onboarding → here → Stripe checkout (7-day trial, $49.99/mo) → `/dashboard`

## Status
Currently "free early access" mode — may bypass this page.

## Related Notes
- [[Auth-Flow]] — Position in signup flow
- [[API-Routes]] — POST /api/stripe/checkout
