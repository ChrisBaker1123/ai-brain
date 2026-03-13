# Admin Dashboard

## Overview
Full-featured analytics dashboard accessible only to the admin account (`apollocontentmgmt@gmail.com`). Located at `/admin` with its own layout and sidebar.

## Access Control
- **Admin Email**: Set via `ADMIN_EMAIL` env var (case-insensitive comparison)
- **Admin User ID**: Set via `ADMIN_USER_ID` env var (UUID match)
- Authorization checked in 4 places:
  1. `(admin)/admin/layout.tsx` — server-side redirect
  2. `(admin)/admin/users/page.tsx` — server-side redirect
  3. `api/admin/metrics/route.ts` — 403 response
  4. `(dashboard)/layout.tsx` — controls sidebar Admin link visibility

## Dashboard Tabs

### Overview
- **Key metrics**: Total Users, Active Today, Total Logins, Longest Streak
- **Secondary metrics**: Template Uses, AI Coach Chats, Favorites Saved, Feedback
- **Charts**: Daily Active Users (30d area), Hourly Login Activity (bar), New Signups (30d line)
- **Lists**: Login Streak Leaderboard, Recent Login Activity

### All Users
- Sortable table: Name, Firm, Tier, Engagement Score, Streak, Logins, Templates, Chats, 7d Activity mini-chart, Last Login
- Searchable by name, firm, tier
- Engagement score (0-100): logins 30%, templates 30%, chat 20%, favorites 10%, feedback 10%

### Activity & Usage
- Template Usage timeline (30d), Category usage bar, Subscription pie, Top Templates, Recent Signups

### Engagement
- Conversion Funnel (5 stages with % rates)
- AI Confidence Levels pie chart
- Engagement Distribution bars
- Feature Adoption cards

## Technical Details
- Client: `admin-charts.tsx` (Recharts)
- API: `GET /api/admin/metrics` (supabaseAdmin service role)
- Auto-refresh: every 5 minutes
- Login tracking: `POST /api/track-login` (debounced 1/hour)
- DB table: `user_login_events` (user_id, logged_in_at, ip_address, user_agent)

## Related
- [[Dashboard]] — sidebar shows Admin link when isAdmin=true
