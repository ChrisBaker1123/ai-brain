# Deployment

#project #deployment

## Platform
**Vercel** — Standard Next.js deployment with serverless functions and edge middleware.

Live URL: https://www.advisorintelligence.app

## Deploy Command
```bash
npx vercel --prod --token REDACTED
```

## Environment Variables (Required)
| Variable | Purpose | Where |
|----------|---------|-------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project URL | Vercel env vars |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anon/public key | Vercel env vars |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase admin key (server-side only) | Vercel env vars (secret) |
| `ANTHROPIC_API_KEY` | Claude API key for AI Coach | Vercel env vars (secret) |

## Environment Variables (Optional / Pending)
| Variable | Purpose | Status |
|----------|---------|--------|
| `ADMIN_EMAIL` | Admin user email for dashboard access | Set |
| `ADMIN_USER_ID` | Admin Supabase user ID | **Needs to be set** |
| `STRIPE_SECRET_KEY` | Stripe API key | Set (for subscription billing) |
| `STRIPE_WEBHOOK_SECRET` | Stripe webhook signature verification | **Needs webhook configured first** |
| `NEXT_PUBLIC_CRISP_WEBSITE_ID` | Crisp chat widget | **Needs Crisp account** |
| `NEXT_PUBLIC_BOOKING_URL` | Cal.com/Calendly embed URL | **Needs booking service** |
| `NEXT_PUBLIC_SUPABASE_GOOGLE_CLIENT_ID` | Google OAuth | **Needs Supabase config** |

## Security Headers (next.config.ts)
- `X-Frame-Options: DENY` — Prevents iframe embedding
- `X-Content-Type-Options: nosniff` — Prevents MIME sniffing
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Strict-Transport-Security: max-age=63072000` — 2-year HSTS with preload
- `Permissions-Policy: camera=(), microphone=(), geolocation=()` — Restrict device APIs

## Pre-Deploy Checklist
1. [ ] Run `npm run build` locally to catch type errors
2. [ ] Verify all env vars are set in Vercel dashboard
3. [ ] Check Supabase RLS policies are applied
4. [ ] Test auth flow (signup → onboarding → dashboard)
5. [ ] Verify API routes respond correctly

## Git Status
- **Local only** — No remote configured (no `origin`)
- **Branch**: `master` (7 commits)
- **Main branch reference**: `main` (does not exist locally)
- Deployment likely uses Vercel CLI direct push, not git-based CI

## Gotchas
- Build requires all Supabase env vars even for pages that don't use them (Next.js pre-renders)
- The deploy token should be passed via `--token` flag, not stored in env
- Tailwind v4 uses `@import "tailwindcss"` syntax, not `@tailwind` directives

## Related Notes
- [[Overview]] — Project context
- [[Tech-Stack]] — Full dependency list
- [[Schema]] — Database that deployment connects to
- [[Auth-Flow]] — Auth requires correct env vars
