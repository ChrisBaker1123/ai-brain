---
type: moc
title: "Map of Content — Advisor Intelligence"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: business
---

# Advisor Intelligence

The main product: a copy-paste AI template toolkit for financial advisors. 68 templates across 8 workflow categories. Gap-filler positioning — "the AI layer for everything your existing systems don't cover."

## Core Product
- [[Overview]] — What it is, business model, current state
- [[Tech-Stack]] — Next.js 16.1.6, React 19, Supabase, Tailwind v4, Claude API
- [[Architecture]] — File tree, route groups, data flow, auth flow
- [[Design-System]] — oklch colors, Plus Jakarta Sans, animations, responsive breakpoints
- [[Deployment]] — Vercel deploy, env vars, security headers

## Decisions That Shape the Product
- [[2026-03-pivot-to-gap-filler]] — From planning functions to workflow categories
- [[2026-03-eight-workflow-categories]] — 8 categories reflecting advisor daily reality
- [[2026-03-remove-analysis-templates]] — 13 system-redundant templates removed
- [[2026-03-copilot-primary-ai]] — Microsoft Copilot as primary AI tool
- [[2026-03-free-early-access]] — Trust-building through free access

## Principles That Guide It
- [[gap-filler-positioning]] — The AI layer for what existing tools don't cover
- [[workflow-not-function]] — Organize by daily workflow, not planning functions
- [[compliance-aware-not-approved]] — Reference regulations, don't replace compliance

## Pages (Route Documentation)
### Marketing
- [[Page-Landing]] — Homepage (~52KB, 16 sections)
- [[Page-Pricing]] — Free early access, future $49.99/mo
- [[Page-About]] — Founder story
- [[Page-Trust]] — Data flow, compliance, security
- [[Page-Compare]] — vs ChatGPT alone
- [[Page-Preview]] — Template previews without login
- [[Page-Book]] — Demo booking

### Auth & Onboarding
- [[Page-Login]] — Email/password + Google OAuth
- [[Page-Reset-Password]] — Password recovery
- [[Page-Profile]] — 2-screen onboarding
- [[Page-Subscribe]] — Stripe paywall

### Dashboard
- [[Page-Dashboard]] — Personalized action cards
- [[Page-Toolkit]] — 68 templates, 8 categories
- [[Page-Documents]] — 20 document templates
- [[Page-Chat]] — AI Coach (Claude streaming)
- [[Page-Scenario-To-Plan]] — 20 action plans
- [[Page-Tutorials]] — 18 how-to guides
- [[Page-Favorites]] — Saved outputs
- [[Page-Admin]] — Analytics, user management

## Components
- [[Component-Prompt-Runner]] — Template copy modal (core UX)
- [[Component-Document-Runner]] — Document copy modal
- [[Component-Dashboard-Shell]] — Sidebar layout
- [[Component-CommandPalette]] — Cmd+K search
- [[Component-SiteTour]] — 10-step interactive tour
- [[Component-Chat-Widget]] — Floating AI Coach

## Database
- [[Schema]] — 9 tables, 15 indexes
- [[Auth-Flow]] — Auth walkthrough
- [[RLS-Policies]] — Row-level security
- [[User-Model]] — Profile fields
- [[API-Routes]] — All API endpoints

## Strategy & Research
- [[Product-Strategy-Pivot]] — Full strategy document
- [[AI-Gap-Analysis]] — Market gaps in advisor AI
- [[Template-Competitive-Analysis]] — Coverage vs competitors
- [[Competitive-Landscape]] — Market positioning
- [[Target-Audience]] — Who we build for

## Brand & Voice
- [[Brand-Voice]] — Voice characteristics, examples, anti-examples
- [[Copy-Inventory]] — All copy, rated
- [[Content-Gaps]] — What's missing
