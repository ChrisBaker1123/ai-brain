# Advisor Intelligence — Knowledge Base

> **Last updated**: 2026-03-13
> **Product**: AI prompt toolkit SaaS for financial advisors
> **Founder**: Christopher Baker (SDSU, San Diego)
> **Live**: https://www.advisorintelligence.app

---

## 01 — Project
- [[Overview]] — What Advisor Intelligence is, business model, current state
- [[Tech-Stack]] — Next.js 16.1.6, React 19, Supabase, Tailwind v4, Claude API
- [[Architecture]] — File tree, route groups, data flow, auth flow, key patterns
- [[Design-System]] — oklch colors, Plus Jakarta Sans, animations, responsive breakpoints
- [[Magic-UI-Components]] — BlurFade, Marquee, NumberTicker, ShimmerButton, AnimatedShinyText, BorderBeam
- [[Deployment]] — Vercel deploy, env vars, security headers, pre-deploy checklist
- [[Target-Audience]] — RIAs, wirehouses, IBDs, pain points, how they find tools
- [[Competitive-Landscape]] — vs ChatGPT, FP Alpha, VRGL, prompt libraries

## 02 — Pages
### Public / Marketing
- [[Page-Landing]] — Homepage (~52KB, 16 sections, all Magic UI components)
- [[Page-Pricing]] — Free early access, future $49.99/mo, comparison section
- [[Page-About]] — Founder story, mission, values
- [[Page-Trust]] — Data flow, compliance framework, security details
- [[Page-Compare]] — vs ChatGPT Alone (SEO-targeted comparison)
- [[Page-Preview]] — Real template/document previews, no login required
- [[Page-Book]] — Demo booking (currently mailto fallback)

### Legal
- [[Page-Terms]] — Terms of Service (March 10, 2026)
- [[Page-Privacy]] — Privacy Policy (March 10, 2026)

### Auth
- [[Page-Login]] — Email/password login + signup (Google OAuth not configured)
- [[Page-Reset-Password]] — 3-step password recovery
- [[Page-Profile]] — 2-screen onboarding (firm type, AUM, specialties, tone)
- [[Page-Subscribe]] — Stripe paywall redirect

### Dashboard
- [[Page-Dashboard]] — Personalized action cards, AI Coach link
- [[Page-Toolkit]] — 61 templates, 11 categories, search + filter
- [[Page-Toolkit-Category]] — Category deep-link redirect
- [[Page-Documents]] — 20 document templates, 6 categories
- [[Page-Chat]] — Full-page AI Coach (Claude streaming via SSE)
- [[Page-Scenario-To-Plan]] — 20 Action Plan scenarios, multi-step workflows
- [[Page-Tutorials]] — 18 How-To Guides, 5 categories, learning path
- [[Page-Tutorial-Slug]] — Individual tutorial view
- [[Page-Quick-Ref]] — Searchable quick reference (470 lines)
- [[Page-Use-Cases]] — AI use case library with compliance notes
- [[Page-Favorites]] — Saved template outputs
- [[Page-History]] — Generation history
- [[Page-Settings]] — Profile editing (currently a stub)

### Admin
- [[Page-Admin]] — Analytics dashboard, user directory, coupon management

## 03 — Components
### Core
- [[Component-Prompt-Runner]] — Template copy modal (337 lines, core UX)
- [[Component-Document-Runner]] — Document copy modal (334 lines)
- [[Component-Dashboard-Shell]] — Sidebar layout wrapper (366 lines)

### Features
- [[Component-CommandPalette]] — Cmd+K search (483 lines)
- [[Component-SiteTour]] — 10-step interactive tour (671 lines)
- [[Component-Chat-Widget]] — Floating AI Coach bubble (263 lines)
- [[Component-Template-Feedback]] — Thumbs up/down widget
- [[Component-PageGuide]] — Per-page onboarding overlay
- [[Component-UpgradeModal]] — Free trial info modal
- [[Component-Logo]] — Logo icon + full wordmark
- [[Component-CrispChat]] — Crisp chat widget (not active)
- [[Component-ThemeProvider]] — Dark/light mode wrapper

### Magic UI
- [[Component-BlurFade]] — Scroll-triggered fade animation
- [[Component-Marquee]] — Continuous scrolling content
- [[Component-NumberTicker]] — Animated counting numbers
- [[Component-ShimmerButton]] — Shimmer spark CTA button
- [[Component-AnimatedShinyText]] — Shimmer text effect
- [[Component-BorderBeam]] — Border gradient beam (removed from UI)

## 04 — Database
- [[Schema]] — 9 tables, 15 indexes, extensions, entity relationships
- [[Auth-Flow]] — Signup, login, OAuth, session management, password reset
- [[RLS-Policies]] — Row-level security for every table
- [[User-Model]] — Profile fields, how data is collected and used
- [[API-Routes]] — All endpoints: chat, favorite, feedback, generate, admin, Stripe

## 05 — Content
- [[Copy-Inventory]] — Every piece of user-facing copy, rated strong/adequate/weak
- [[Brand-Voice]] — Voice characteristics, 10 good examples, 10 anti-examples
- [[SEO-Audit]] — Page titles, missing elements, keyword opportunities
- [[Content-Gaps]] — Missing pages, content types, social proof roadmap

## 06 — Marketing
- [[Marketing-Strategy]] — Channels, growth levers, positioning, metrics
- [[LinkedIn-Playbook]] — 10 post frameworks, schedule, engagement tactics
- [[Email-Strategy]] — 5-email onboarding sequence, nurture, re-engagement
- [[Content-Calendar]] — Weekly template, monthly priorities, blog post ideas
- [[Outreach-Playbook]] — Cold email templates, LinkedIn sequences, conference strategy

## 07 — Roadmap
- [[Current-Sprint]] — Active work and recently completed
- [[Backlog]] — Prioritized backlog (24 items)
- [[Ideas]] — Raw ideas with effort/impact estimates
- [[DLK-Engagement]] — ~$350M AUM RIA prospect, Solana Beach
- [[White-Label-Platform]] — Custom branded platform concept
- [[Client-Pipeline]] — All prospects and contacts

## 08 — Session Logs
- [[2026-03-13-Vault-Build]] — This session: full analysis + vault creation
- [[CHANGELOG]] — All project changes by date
- [[SESSION-LOG]] — MCPs, analysis, decisions per session
