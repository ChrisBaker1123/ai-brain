# Changelog

## 2026-03-16
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
