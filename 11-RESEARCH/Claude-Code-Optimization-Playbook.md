---
title: "Claude Code Optimization Playbook"
type: reference
date: 2026-03-16
domain: meta
tags: [claude-code, optimization, playbook, reference]
---

# Claude Code Optimization Playbook

> Permanent reference for operating this Claude Code instance at maximum effectiveness.
> **Last audit**: 2026-03-16 | **Next audit**: 2026-04-16

---

## Complete Inventory

### MCPs (11 active, 5 removed)

| MCP | Purpose | When to Use | Context Cost |
|-----|---------|-------------|--------------|
| supabase | Database operations | Schema, RLS, user queries, migrations | Medium |
| playwright | Browser automation | Visual QA, testing, screenshots | Medium |
| github | Git operations | PRs, issues, code search | Low |
| shadcn | UI components | Adding new shadcn/ui components | Low |
| magicui | Animations | Adding Magic UI components | Low |
| context7 | Library docs | Looking up Next.js, React, Tailwind docs | Low |
| brave-search | Web search | Research, competitor intel, market data | Low |
| firecrawl | Web scraping | Extracting content from web pages | Low |
| obsidian | Vault access | Reading vault notes (writes may hang) | Low |
| next-devtools | Next.js tools | Debugging Next.js specific issues | Low |
| vercel | Deployment | Managing Vercel deployments | Low |

**Removed (2026-03-16)**:
- `sequential-thinking` — redundant with Opus built-in thinking
- `memory` — redundant with auto-memory system
- `fetch` — redundant with WebFetch tool
- `context-mode` — unclear value, unused
- `resend` — empty API key, non-functional

### Skills (5 custom + 14 framework)

| Skill | Triggers On | Quality |
|-------|------------|---------|
| ai-marketing | "LinkedIn post", "blog", "email sequence", "marketing" | Good — updated for pivot |
| site-audit | "test site", "QA", "check deployment", "audit" | Good — updated for pivot |
| content-creator | "write blog", "create guide", "documentation" | Good — updated for pivot |
| advisor-outreach | "cold email", "outreach", "prospecting", "demo script" | Good — updated for pivot |
| deploy | "deploy", "ship", "push to prod", "go live" | New — build+deploy+verify |

Framework skills: brand-guidelines, canvas-design, doc-coauthoring, frontend-design, internal-comms, landing-page-generator, mcp-builder, skill-creator, theme-factory, voice-refine, web-artifacts-builder, webapp-testing, claude-api, simplify

### Agents (21 total)
- 12 GSD agents (gsd-planner, gsd-executor, gsd-verifier, etc.)
- 9 generic (code-reviewer, security-auditor, test-writer, output-evaluator, architecture-reviewer, devops-sre, implementer, planner, guide-reviewer)

### Hooks (7 total)

| Hook | Event | Purpose |
|------|-------|---------|
| dangerous-actions-blocker.sh | PreToolUse | Block rm -rf, force push, sensitive file edits |
| auto-format.sh | PostToolUse (Write/Edit) | Auto-format with Prettier |
| output-secrets-scanner.sh | PostToolUse | Detect leaked secrets |
| pre-compact.sh | PreCompact | Save state before compaction |
| gsd-check-update.js | SessionStart | GSD version check |
| gsd-context-monitor.js | PostToolUse | GSD context tracking |
| gsd-statusline.js | StatusLine | GSD status display |

### Cron Jobs

| Schedule | Script | Budget | Purpose |
|----------|--------|--------|---------|
| Every 10 min | vault git sync | Free | Auto-commit obsidian vault |
| Every 6 hours | site-monitor.sh | $0.30 | Check 3 pages load correctly |
| Daily 1 PM UTC | daily-content.sh | $1.50 | 3 LinkedIn + 1 blog + 1 email |
| Sunday 3 PM UTC | weekly-strategy.sh | $3.00 | Site audit + competitor check |

**Critical**: Crons require active OAuth. If logs show "OAuth token expired", run `claude /login` to re-authenticate.

---

## Session Startup Checklist by Task Type

### Quick Fix (~15 min)
1. Read CLAUDE.md (auto-loaded)
2. Read relevant source file
3. Fix → Build → Deploy if needed

### Feature Build (~60 min)
1. Read [[Architecture]], relevant [[02-PAGES]] note
2. Plan approach (use Plan Mode for >3 files)
3. Implement → Build → Test → Deploy
4. Update vault page note if structure changed

### Content Creation (~30 min)
1. Read [[Research-Digest]] (ALWAYS first)
2. Read [[Brand-Voice]] and [[Advisor-Language-Bank]]
3. Use ai-marketing or content-creator skill
4. Save to ~/obsidian-vault/09-CONTENT-DRAFTS/
5. Update [[Content-Calendar]]

### Debugging (~30 min)
1. Read error + relevant source files
2. Use Grep to find related code
3. Fix → Build → Verify
4. Document if pattern is new

### Research (~30 min)
1. Read [[Research-Digest]] for current state
2. Use brave-search for web research
3. Synthesize findings
4. Save to ~/obsidian-vault/11-RESEARCH/
5. Update [[Research-Digest]] if significant

### Client/Prospect Work (~20 min)
1. Read [[Client-Pipeline]] for status
2. Read specific contact file in [[12-CONTACTS/]]
3. Read [[DLK-Engagement]] or relevant engagement note
4. Use advisor-outreach skill if creating outreach

---

## Context Management Rules

### What to Read
- **Always loaded**: CLAUDE.md, MEMORY.md (auto)
- **Read on demand**: Specific vault notes by task type (see checklist above)
- **Never**: Entire ~/obsidian-vault directory at once

### When to Compact
- /compact at 70% context usage
- After compaction, re-state current task
- Use subagents for parallel research to protect main context

### When to Use Subagents
- Research tasks requiring 3+ web searches
- Parallel independent investigations
- Reading multiple large files to synthesize
- Running tests while continuing other work

---

## When to Use GSD vs Direct Prompts

**Use GSD** when:
- Multi-phase project spanning several sessions
- Need persistent state tracking across context resets
- Complex features requiring research → plan → execute → verify cycle
- Want atomic commits and progress tracking

**Use direct prompts** when:
- Quick fixes (< 30 min)
- Single-file changes
- Content creation tasks
- Research and synthesis
- Most daily tasks

---

## Common Mistakes and Prevention

| Mistake | Prevention |
|---------|------------|
| SCSU instead of SDSU | CLAUDE.md "Do NOT" rule |
| first_name instead of full_name | CLAUDE.md rule + will cause DB error |
| asChild instead of render | CLAUDE.md rule — it's @base-ui/react |
| Fake social proof | CLAUDE.md rule + memory feedback |
| localStorage in useState | Will cause SSR hydration error |
| Reading whole vault | Targeted file reads only |
| Stale Research-Digest.md | Update after any product changes |
| Cron auth expiration | Check logs regularly, re-login |
| Positioning as replacement | Always "complements" and "fills the gap" |

---

## Monthly Maintenance Checklist

### Quick (5 min)
- [ ] Check cron logs: `ls -la ~/marketing-agents/logs/ | tail -5`
- [ ] Verify CLAUDE.md < 120 lines
- [ ] Verify MEMORY.md < 50 lines
- [ ] Check crontab: `crontab -l`

### Standard (15 min)
- [ ] Review CLAUDE.md against current codebase
- [ ] Review memory files for stale info
- [ ] Check [[Research-Digest]] is current (template count, categories, positioning)
- [ ] Check [[Current-Sprint]] priorities are accurate
- [ ] Verify skill descriptions still auto-trigger correctly

### Deep (30 min)
- [ ] Review cron output quality (are posts usable?)
- [ ] Check site-monitor logs for recurring issues
- [ ] Run context budget calculator
- [ ] Consider adding/removing hooks based on recent issues
- [ ] Check for new Claude Code features in changelog

---

## Key Metrics

| Metric | Current | Target |
|--------|---------|--------|
| CLAUDE.md tokens | ~1,200 | < 2,000 |
| MCPs connected | 11 | 8-12 |
| Custom skills | 5 | 5-7 |
| Cron daily cost | ~$2.70 | < $5/day |
| Cron weekly cost | ~$22 | < $30/week |

---

## Related Notes
- [[Current-Sprint]] — Active work priorities
- [[Self-Improvement-Playbook]] — Previous optimization (2026-03-15)
- [[Architecture]] — Project structure
- [[Research-Digest]] — Condensed intel brief
