# Page: Landing (Homepage)

#page #marketing

## Route
`/` — Root page, public

## Purpose
Primary marketing page. Converts visitors to signups. Showcases all platform features.

## Layout
Root layout only (no marketing layout wrapper). ~52KB file — the largest page in the app.

## Sections (Top to Bottom)
1. **Navigation bar** — Logo + "Advisor Intelligence", links: See It In Action, Pricing, About, Trust, Sign in, Get Started (blue button)
2. **Hero** — Badge: "BUILT FOR RIAs, WIREHOUSES & HYBRID FIRMS" with sparkle. H1: "Your personal AI coach for your advisory practice." Blue accent on second line. Two CTAs: "Get Started Free" (blue) + "See How It Works" (outline). Note: "Free during early access - No credit card required"
3. **Trust strip** — [[Component-Marquee]] scrolling firm types: Independent RIAs, Wirehouses, Broker-Dealers, Hybrid Firms, Solo Practices, Family Offices, Multi-Advisor Teams, Ensemble Practices. Text: "Designed for advisors at every firm type."
4. **Five tools section** — "Five tools. One platform." Five feature cards: AI Templates (60+), Document Builder (NEW), How-To Guides, Deep Analysis (POWER), Action Plans (NEW with CTA)
5. **See it in action** — "Proof, not promises." Multi-Generational Wealth Transfer Planner example. Side-by-side: Without AI (2-3 hrs) vs. With AI (3 min). Detailed sample output excerpt.
6. **How it works** — Three numbered steps: Find template → Paste with context → Get polished output
7. **AI coaching section** — "Not sure where to start?" Three cards: Guides, Workflows, Context
8. **Category showcase** — 11 clickable category links with template counts
9. **Data safety notice** — Single line: "Your data stays yours" with link to /trust
10. **Document Builder** — "The documents your clients actually read." Four document type cards.
11. **Stats strip** — [[Component-NumberTicker]] — 60+, 11, 20+, 38, <2 min
12. **Pricing preview** — "Free during early access." Single card with full feature list.
13. **FAQ** — 5 collapsible questions
14. **Bottom CTA** — "Ready to use AI with confidence?"
15. **Footer** — Full multi-column: Product, Company, For Advisors. "Built by Christopher Baker - San Diego, CA"
16. **Sticky bottom bar** — "AI templates for financial advisors. Free during early access." with CTA

## Components Used
- [[Component-ShimmerButton]] — Primary CTA
- [[Component-NumberTicker]] — Stats section counters
- [[Component-Marquee]] — Trust strip firm types
- [[Component-BlurFade]] — All section animations
- [[Component-AnimatedShinyText]] — Hero badge
- [[Component-Logo]] — Navigation and footer

## Supabase Dependencies
None — fully static public page

## Auth Requirements
Public (no auth needed)

## Current State Assessment
- **Strong**: Comprehensive, professional design. Good section flow. Honest copy (no fake metrics/testimonials). Realistic sample output.
- **Weak**: Page is very large (~52KB). Stats strip numbers may not render in accessibility tree. No A/B testing.
- **Note**: "Sarah Chen, CFP at Clarity Wealth Advisors" in sample output — this is a fictional example, not a testimonial

## SEO
- **Title**: "AI Templates for Financial Advisors | Advisor Intelligence"
- **Missing**: Structured data (FAQ schema), og:image, canonical URL

## Related Notes
- [[Page-Pricing]] — Linked from pricing section
- [[Page-About]] — Linked from footer
- [[Page-Trust]] — Linked from data safety section
- [[Page-Login]] — CTA destination
- [[Design-System]] — Visual language showcase
- [[Magic-UI-Components]] — All animations used here
