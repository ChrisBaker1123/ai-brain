---
type: log
title: "Changelog"
status: active
created: 2026-03-13
updated: 2026-03-16
domain: business
---

# Changelog

## 2026-03-24

- **Deep knowledge build** (vault expansion session):
  - Expanded [[10-INDUSTRY/RIA-Economics|RIA Economics]] with market size, margins, team structures, time value economics (sourced: Schwab, Raymond James, Fidelity, Kitces)
  - Expanded [[10-INDUSTRY/AI-Adoption-Data|AI Adoption Data]] with Schwab Jan 2026 study, 63% adoption rate, tool usage breakdown, barrier data
  - Expanded [[10-INDUSTRY/Advisor-Workflow|Advisor Workflow]] with per-meeting overhead breakdown, DLK person-by-person needs, industry benchmarks
  - Expanded [[10-INDUSTRY/Regulatory-Landscape|Regulatory Landscape]] with SEC rule withdrawal, enforcement actions, compliance checklist
  - Filled 7 competitor stubs: [[10-INDUSTRY/Competitor-Tools/Hazel|Hazel]], [[10-INDUSTRY/Competitor-Tools/Jump|Jump]], [[10-INDUSTRY/Competitor-Tools/Agentforce|Agentforce]], [[10-INDUSTRY/Competitor-Tools/Zeplyn|Zeplyn]], [[10-INDUSTRY/Competitor-Tools/Pulse360|Pulse360]], [[10-INDUSTRY/Competitor-Tools/CogniCor|CogniCor]], [[10-INDUSTRY/Competitor-Tools/FP-Alpha|FP Alpha]]
  - Created 4 new competitor profiles: [[10-INDUSTRY/Competitor-Tools/Zocks|Zocks]], [[10-INDUSTRY/Competitor-Tools/Conquest-Planning|Conquest]], [[10-INDUSTRY/Competitor-Tools/GReminders|GReminders]], [[10-INDUSTRY/Competitor-Tools/Altitude-CRM|Altitude CRM]]
  - Created [[10-INDUSTRY/Competitor-Tools/Zocks-vs-Jump-Comparison|Zocks vs Jump Comparison]] — detailed feature comparison for DLK
  - Created [[10-INDUSTRY/AI-Implementation-Failure-Rates|AI Implementation Failure Rates]] — MIT, RAND, S&P Global data
  - Expanded [[15-SALESFORCE/FSC-Features|Salesforce FSC]] with full pricing, overlays, underutilized features, AI integration paths
  - Created [[15-SALESFORCE/n8n-Salesforce-Integration|n8n Salesforce Integration]] — setup guide
  - Expanded [[00-ADVISOR-INTELLIGENCE/Pricing-Framework|Pricing Framework]] with market comparables, fractional exec context, ROI math
  - Expanded [[00-ADVISOR-INTELLIGENCE/Tech-Stack|Tech Stack]] with n8n architecture, meeting notes pipeline, prompt engineering
  - Created [[00-ADVISOR-INTELLIGENCE/Business-Infrastructure|Business Infrastructure]] — LLC, banking, insurance, pending setup
  - Created [[00-ADVISOR-INTELLIGENCE/n8n-Deployment-Guide|n8n Deployment Guide]] — Docker production setup
  - Created [[00-ADVISOR-INTELLIGENCE/CA-Licensing-Research|CA Licensing Research]] — California requirements
  - Created [[00-ADVISOR-INTELLIGENCE/EO-Insurance-Research|E&O Insurance Research]] — Coverage options
  - Created [[08-REFERENCE/market-research/SEC-API-Evaluation|SEC API Evaluation]] — sec-api.io pricing/features
  - Expanded DLK people profiles: [[20-CLIENTS/DLK/People/Don-Dempster|Don]], [[20-CLIENTS/DLK/People/Mark-Halby|Mark]], [[20-CLIENTS/DLK/People/Ted-Research|Ted]], [[20-CLIENTS/DLK/People/Brian-Trading|Brian]], [[20-CLIENTS/DLK/People/Tom-CFP|Tom]]
  - Expanded [[20-CLIENTS/DLK/Workflows/WF-Backlog|DLK Workflow Backlog]] with fee audit and CPA outreach details

- **Session journaling system** (new vault section):
  - Created `30-SESSION-JOURNAL/` folder structure
  - Created [[30-SESSION-JOURNAL/INDEX|Journal Index]] — reverse-chronological session records
  - Created [[30-SESSION-JOURNAL/LEARNINGS|Accumulated Learnings]] — distilled insights across all sessions
  - Created retroactive entries for 2026-03-23 and 2026-03-24
  - Added session journal rule to [[CLAUDE.md|vault CLAUDE.md]]

- **Cross-link audit and MOC updates**:
  - Updated [[00-MAPS/INDEX|Master Index]] — added 30-SESSION-JOURNAL, updated counts
  - Updated [[MOC-Advisor-Intelligence]] — consulting model language, all competitor links, industry ring links
  - Updated [[MOC-Research]] — added 10-INDUSTRY competitor section, technical research section
  - Updated [[Competitive-Landscape]] — corrected pricing, added Zocks, expanded comparison table
  - Updated [[Current-Sprint]] — DLK Week 1 plan, infrastructure setup, vault expansion checkoff
  - Updated [[00-MAPS/CHANGELOG|Changelog]] — this entry
  - Created [[99-META/Obsidian-Professional-Practices|Obsidian Professional Practices]] — vault best practices research

- **Web research** (7 topics via brave-search):
  - sec-api.io pricing and capabilities
  - Zocks vs Jump detailed comparison
  - n8n Salesforce node documentation
  - n8n Docker production deployment
  - California tech consultant licensing
  - Next Insurance E&O coverage
  - Obsidian professional vault practices

## 2026-03-23

- **Hub-and-spoke vault restructure** (~57 files):
  - Created 00-ADVISOR-INTELLIGENCE/ (sun) with business model, pricing, sales, compliance, templates
  - Created 20-CLIENTS/DLK/ (first planet) with hub, people, workflows, compliance, tech stack, deliverables
  - Created 10-INDUSTRY/ (ring) with RIA economics, AI adoption, regulatory, competitor stubs
  - Created 15-SALESFORCE/ (ring) with FSC features, Flow patterns
  - Built prospecting system at ~/advisor-intelligence/dlk-prospecting/

## 2026-03-16
- **Connected AI positioning research** (vault creation session):
  - Created [[Connected-AI-Trend]] — Industry analysis, Morgan Stanley/Altruist/Hazel context, gap analysis, positioning evolution
  - Created [[Connected-AI-Implementation-Plan]] — Technical roadmap for Phase 2 (CRM integration), Phase 3 (connected workflows), schema design, security model
  - Updated [[Research-Digest]] — Added "Connected AI Positioning" section with key messaging
  - Updated [[Current-Sprint]] — Added connected AI positioning as item 2 in next-up roadmap
  - Updated [[INDEX.md]] — Added two new research files to Strategy subsection

- **Comprehensive self-optimization** (deep audit session):
  - CLAUDE.md rewrite: Added gap-filler positioning, architecture map, full MCP table (11 servers), skills table, vault context rules by task type, active clients section. ~120 lines, ~1200 tokens.
  - Removed 5 redundant MCPs: sequential-thinking, memory, fetch, context-mode, resend (empty API key)
  - Created deploy skill (build → test → deploy → verify pipeline)
  - Installed dangerous-actions-blocker.sh (PreToolUse security hook)
  - Updated all 4 custom skills (ai-marketing, site-audit, content-creator, advisor-outreach) with post-pivot content
  - Fixed auto-format hook Prettier path resolution
  - Created global ~/.claude/CLAUDE.md with personal preferences
  - Updated Research-Digest.md for post-pivot accuracy (68 templates, 8 categories)
  - Fixed cron scripts with auth checks and error handling
  - Updated MEMORY.md with deploy skill and cron auth note
  - Created [[Claude-Code-Optimization-Playbook]] — comprehensive system reference
  - Updated [[Current-Sprint]] and [[CHANGELOG]]
  - Note: All cron scripts failing since ~March 14 due to OAuth token expiration

## 2026-03-15
- System self-evaluation and optimization session
- CLAUDE.md rewrite: 110→76 lines, 1540→961 tokens (removed architecture tree, targeted vault reads)
- Memory cleanup: MEMORY.md 172→42 lines, fixed SCSU→SDSU bug, removed duplicate user file
- Cron optimization: removed 4 dead tmux entries, vault sync 2min→10min, tightened budgets
- Hooks added: auto-format.sh (PostToolUse), output-secrets-scanner.sh (PostToolUse)
- Vault INDEX.md updated with 5 missing research notes
- Created [[Self-Improvement-Playbook]] — system optimization reference

## 2026-03-14
- Product Strategy Pivot: full template audit (61→68 templates, 11→8 categories)
- 13 templates removed, 18 rethought, 20 new templates created
- Created [[Product-Strategy-Pivot]] and [[Template-Pivot-Implementation]]

## 2026-03-13
- Built Obsidian knowledge base vault with 60+ notes across 9 sections
- Analyzed full codebase, Supabase schema, live site, git history
- Documented all pages, components, database tables, RLS policies, API routes
- Created marketing strategy, LinkedIn playbook, email sequences, outreach playbook
- Identified [[Backlog]] items: pending env vars, SEO gaps, content needs
- Identified risk: [[Page-About]] bio implies more experience than founder has

## 2026-03-12
- Overhauled admin dashboard with Recharts charts
- Added discount code management via Stripe API ([[Page-Admin]])
- Built Stripe integration: checkout, webhook, portal routes
- Added 7-day free trial flow at $49.99/mo

## 2026-03-11
- Expanded to 11 categories, 61 templates (added deep_analysis with 8 prompts)
- Added Document Builder (20 templates, 6 categories)
- Added AI Academy / How-To Guides (18 tutorials, 5 categories)
- Redesigned prompt UX: instant-copy model, profile auto-injection
- Simplified dashboard: personalized action cards, no clutter
- Changed color scheme to warm neutral backgrounds (hue 80)
- Swapped body font to Plus Jakarta Sans
- Added Action Plans (scenario-to-plan feature)
- Removed fake social proof and inflated metrics

## 2026-03-10
- Initial app build: Next.js + Supabase + Tailwind
- Auth flow: email/password + Google OAuth (not configured)
- Landing page, pricing, about, trust, compare, preview pages
- Legal pages: terms, privacy (dated March 10, 2026)
- Command palette, site tour, chat widget
