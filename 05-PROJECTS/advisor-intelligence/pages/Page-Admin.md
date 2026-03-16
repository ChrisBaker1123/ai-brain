# Page: Admin Dashboard

#page #admin

## Routes
- `/admin` — Analytics dashboard
- `/admin/users` — User directory
- `/admin/coupons` — Discount code management

## Auth
`ADMIN_EMAIL` or `ADMIN_USER_ID` env var check. Admin bypasses paywall.

## Layout
Admin layout with sidebar (Dashboard, Users, Coupons)

## Dashboard (/admin)
- Recharts charts: signups timeline, generation timeline, category usage bar, tier pie
- Metrics: total users, MRR, generations, 7-day active, chat messages, favorites
- Streak leaderboard (top 10), recent signups/logins
- Auto-refresh every 5 min via `/api/admin/metrics`

## Users (/admin/users)
- Sortable table: name, firmType, aum, tier, streak, totalLogins, lastLogin, generations, joinDate
- Search/filter

## Coupons (/admin/coupons)
- Create Stripe coupons + promotion codes
- List/deactivate active codes
- Stripe API integration

## Related Notes
- [[API-Routes]] — Admin API endpoints
- [[Schema]] — Tables queried
- [[Overview]] — Business metrics
