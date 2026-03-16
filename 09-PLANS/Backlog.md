# Backlog

#roadmap #backlog

## High Priority
0. **Product Strategy Pivot implementation** — Reorganize templates from 11 planning-function categories to 8 workflow categories. Remove 13 system-redundant templates. Reframe 18 templates. Build 19 new gap-filler templates. See [[Product-Strategy-Pivot]].
1. **Configure Stripe webhook** — Set `STRIPE_WEBHOOK_SECRET` env var after configuring webhook in Stripe Dashboard. Blocks payment processing.
2. **Set ADMIN_USER_ID** — In Vercel env vars. Currently relying on ADMIN_EMAIL only.
3. **Google OAuth** — Configure in Supabase, set `NEXT_PUBLIC_SUPABASE_GOOGLE_CLIENT_ID`.
4. **Email sequences** — Set up Resend, configure `RESEND_API_KEY`, build onboarding sequence. See [[Email-Strategy]].
5. **Blog** — Create blog section for SEO. First post: "Why We Reorganized Our Templates." See [[Content-Calendar]].
6. **Booking integration** — Set up Cal.com/Calendly, configure `NEXT_PUBLIC_BOOKING_URL`. See [[Page-Book]].

## Medium Priority
7. **Crisp chat** — Create Crisp account, set `NEXT_PUBLIC_CRISP_WEBSITE_ID`. See [[Component-CrispChat]].
8. **Settings page** — Currently a stub. Build full profile editing form. See [[Page-Settings]].
9. **SEO improvements** — FAQ schema, og:image, sitemap.xml, robots.txt. See [[SEO-Audit]].
10. **Firm-type landing pages** — `/for-rias`, `/for-wirehouses`, `/for-broker-dealers`. See [[Content-Gaps]].
11. **About page bio** — Rewrite to be honest about founder background. See [[Copy-Inventory]].
12. **Footer consistency** — Compare page has full footer, others have simple footer.
13. **Stats strip accessibility** — Numbers may not render in accessibility tree. See [[Page-Landing]].

## Low Priority
14. **Video walkthrough** — Product demo video for landing page
15. **Comparison pages** — vs FP Alpha, vs free prompt libraries
16. **Public changelog** — Show product updates
17. **Status page** — Replace static "All systems operational" with real status
18. **Login autocomplete** — Fix console warning about missing autocomplete attributes
19. **Data export** — Let users export their data (settings page)
20. **Account deletion** — GDPR compliance, delete account and all data

## Technical Debt
21. **Legacy tables** — `prompts`, `template_versions`, `toolkits` tables have 0 rows and are unused. Consider removing.
22. **Rate limiting** — Replace in-memory limiter (999999) with Redis/Supabase for production.
23. **Git remote** — No remote configured. Set up GitHub repo and CI/CD.
24. **Input autocomplete** — Add autocomplete attributes to login form inputs.

## Related Notes
- [[Current-Sprint]] — What's active now
- [[Ideas]] — Raw ideas
- [[Deployment]] — Env var setup
- [[SEO-Audit]] — SEO tasks
- [[Content-Gaps]] — Content to create
