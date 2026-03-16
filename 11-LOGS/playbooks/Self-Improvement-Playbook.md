# Self-Improvement Playbook

#meta #optimization #reference

> Reference document for Claude Code system optimization. Run quarterly or after major project changes.

## Current Setup Inventory (as of 2026-03-15)

### CLAUDE.md
- **Location**: `/home/claude-agent/advisor-intelligence/CLAUDE.md`
- **Size**: 76 lines, ~961 tokens — LEAN budget
- **Score**: 17/20 on context engineering eval
- **Key improvement**: Replaced "read whole vault" with targeted file references

### MCPs Connected
| MCP | Status | Usage |
|-----|--------|-------|
| supabase | Active | Schema, RLS, user data |
| playwright | Active | Site testing, screenshots, visual QA |
| github | Active | Commits, PRs |
| magicui | Active | Animation components |
| shadcn | Active | UI components |
| context7 | Active | Library docs |
| obsidian | Partially working | Reads work, writes hang (use bash) |
| brave-search | Active | Web research |
| fetch | Active | Web page fetching |
| firecrawl | Active | Web scraping |

### Skills (4 custom + 14 framework)
Custom:
- `ai-marketing` — LinkedIn, brand voice, compliance, email/blog
- `site-audit` — Full site QA checklist with playwright
- `content-creator` — Blog/SEO/AEO content
- `advisor-outreach` — Cold outreach campaigns

Framework (GSD + ultimate guide):
- `brand-guidelines`, `canvas-design`, `doc-coauthoring`, `frontend-design`, `internal-comms`, `landing-page-generator`, `mcp-builder`, `skill-creator`, `theme-factory`, `voice-refine`, `web-artifacts-builder`, `webapp-testing`

### Agents (21 total)
- 12 GSD agents (gsd-planner, gsd-executor, gsd-verifier, etc.)
- 9 generic agents (code-reviewer, security-auditor, test-writer, etc.)
- All framework-level, no dead weight

### Hooks
| Hook | Event | Purpose |
|------|-------|---------|
| gsd-check-update.js | SessionStart | GSD version check |
| gsd-context-monitor.js | PostToolUse | GSD context tracking |
| gsd-statusline.js | StatusLine | GSD status display |
| auto-format.sh | PostToolUse (Write/Edit) | Auto-format after edits |
| output-secrets-scanner.sh | PostToolUse | Detect leaked secrets |

### Cron Jobs
| Schedule | Script | Budget | Purpose |
|----------|--------|--------|---------|
| Every 10 min | vault git sync | Free | Auto-commit obsidian vault |
| Every 6 hours | site-monitor.sh | $0.30 | Check 3 pages load correctly |
| Daily 1 PM UTC | daily-content.sh | $1.50 | 3 LinkedIn + 1 blog + 1 email |
| Sunday 3 PM UTC | weekly-strategy.sh | $3.00 | Site audit + competitor check |

**Estimated daily cost**: ~$1.50 (content) + ~$1.20 (4x monitor) = ~$2.70/day
**Estimated weekly cost**: ~$2.70 × 7 + $3.00 (weekly) = ~$21.90/week

### Memory
- MEMORY.md: 42 lines (was 172 — trimmed 76%)
- 6 memory files: 1 user, 3 feedback, 1 reference, 1 (deleted duplicate)

---

## What's Working Well

1. **CLAUDE.md is lean** — 961 tokens, well under 2K threshold. Claude follows rules consistently.
2. **Custom skills trigger correctly** — ai-marketing, site-audit, content-creator, advisor-outreach all auto-trigger on the right prompts.
3. **Cron content generation** — Daily content agent produces usable LinkedIn posts and blog outlines.
4. **Site monitoring** — Every 6 hours, catches issues before users do.
5. **Obsidian vault structure** — 149+ notes, well-organized, research digest provides condensed context.
6. **Anti-pattern rules** — "Do NOT" section prevents the SCSU, first_name, Radix, fake social proof mistakes.

## What Was Changed (2026-03-15)

| Change | Why |
|--------|-----|
| Fixed SCSU → SDSU in memory files | Critical bug: memory was contradicting CLAUDE.md |
| Removed duplicate user_chris_baker.md | Redundant — had user_christopher_baker.md |
| Updated vault reference (77 → 149+ notes) | Stale count caused confusion |
| Fixed deployment URL in MEMORY.md | Was using old Vercel URL |
| CLAUDE.md: Removed architecture tree | Derivable from codebase, saved 30 lines |
| CLAUDE.md: "Brain" → "Context & Vault" | Targeted reads instead of "read whole vault" |
| CLAUDE.md: Removed Vercel MCP | Not actually connected |
| MEMORY.md: 172 → 42 lines | Removed duplicated/derivable information |
| Cron: Removed 4 dead tmux entries | Agent team not running |
| Cron: Vault sync 2min → 10min | Reduce noisy git history |
| Cron: Specific file reads in prompts | Was "read ~/obsidian-vault for full context" — too expensive |
| Cron: Tightened budgets | daily $2→$1.50, weekly $5→$3, monitor $0.50→$0.30 |
| Hooks: Added auto-format.sh | Auto-format after edits (Prettier) |
| Hooks: Added output-secrets-scanner.sh | Catch leaked secrets in output |
| INDEX.md: Added 5 missing research notes | Strategy and pivot notes weren't linked |

## Best Practices Discovered

### From claude-code-ultimate-guide
1. **Context budget < 10K tokens** — beyond this, Claude starts deprioritizing rules. We're at 961.
2. **Rules not documentation** — CLAUDE.md should be actionable rules, not reference docs. Put docs in vault.
3. **Specific file reads** — Never "read entire directory." Always specify exact files.
4. **Hooks for quality gates** — auto-format, secrets scanning, dangerous action blocking.
5. **Session summary hook** — Track costs and session analytics (future improvement).
6. **Canary checks** — Periodically test that Claude follows CLAUDE.md rules (run eval-questions.yaml).
7. **Profile-based context assembly** — For teams, use per-developer profiles. Less relevant for solo projects.

### From Operational Experience
1. **Memory should be < 50 lines** — beyond that, it's duplicating CLAUDE.md or the codebase.
2. **Cron prompts need specific file paths** — "read vault" wastes tokens on 149 notes.
3. **Dead cron entries waste nothing but attention** — remove them to reduce cognitive overhead.
4. **Vault auto-sync every 2 min is too noisy** — 10 min is sufficient, reduces git history by 5x.
5. **Research-Digest.md is the key efficiency tool** — 102 lines that replace reading 38+ research notes.

## Optimization Checklist (Run Monthly)

### Quick (5 min)
- [ ] Run context budget calculator: `bash ~/claude-ultimate-guide/examples/context-engineering/context-budget-calculator.sh ~/advisor-intelligence`
- [ ] Check CLAUDE.md < 100 lines
- [ ] Check MEMORY.md < 50 lines
- [ ] Verify crontab has no dead entries: `crontab -l`
- [ ] Check cron logs exist and are recent: `ls -la ~/marketing-agents/logs/ | tail -5`

### Standard (15 min)
- [ ] Review CLAUDE.md against current codebase (any deprecated rules?)
- [ ] Review memory files for stale information
- [ ] Run vault orphan check: `find ~/obsidian-vault -name "*.md" | while read f; do basename=$(basename "$f" .md); grep -rlq "\[\[$basename" ~/obsidian-vault/00-INDEX/INDEX.md || echo "NOT IN INDEX: $f"; done`
- [ ] Check skill descriptions still auto-trigger correctly
- [ ] Review Research-Digest.md — is it current?
- [ ] Check Current-Sprint.md — are priorities accurate?

### Deep (30 min)
- [ ] Score CLAUDE.md against eval-questions.yaml (target: 16+/20)
- [ ] Run canary check: `bash ~/claude-ultimate-guide/examples/context-engineering/canary-check.sh ~/advisor-intelligence`
- [ ] Review cron output quality — are LinkedIn posts usable? Blog outlines good?
- [ ] Check site-monitor logs for patterns — any recurring issues?
- [ ] Consider adding/removing hooks based on recent session problems

## Common Mistakes and How to Avoid Them

| Mistake | Symptom | Prevention |
|---------|---------|------------|
| SCSU instead of SDSU | Cri's university wrong in output | CLAUDE.md "Do NOT" rule + memory fix |
| first_name instead of full_name | Runtime error | CLAUDE.md rule + ESLint could catch |
| asChild instead of render | shadcn components break | CLAUDE.md rule |
| Fake social proof | "500+ advisors" in output | CLAUDE.md rule + memory feedback |
| localStorage in useState | SSR hydration error | CLAUDE.md rule |
| Reading whole vault | Expensive, slow sessions | Targeted file reads in CLAUDE.md |
| Stale memory | Contradicts reality | Monthly review checklist |

## Session Patterns

### Quick Fix (~15 min, < $0.50)
Read: CLAUDE.md only (auto-loaded)
Tools: Edit, Bash (build check)
Pattern: Read file → Fix → Build → Deploy

### Content Creation (~30 min, < $1.00)
Read: Research-Digest.md, Brand-Voice.md, Content-Calendar.md
Tools: ai-marketing skill, Write
Pattern: Read context → Generate → Save to vault

### Feature Build (~60 min, < $2.00)
Read: CLAUDE.md, relevant component/page files
Tools: Read, Edit, Write, Bash (build)
Pattern: Understand → Plan → Implement → Build → Test → Deploy

### Debug Session (~30 min, < $1.00)
Read: CLAUDE.md, error logs, relevant source files
Tools: Read, Grep, Edit, Bash (build + run)
Pattern: Reproduce → Isolate → Fix → Verify

### Site Audit (~45 min, < $1.50)
Read: Design-System.md, Brand-Voice.md
Tools: site-audit skill, playwright MCP
Pattern: Navigate pages → Screenshot → Compare → Fix → Deploy

### Research Session (~30 min, < $1.50)
Read: Research-Digest.md, relevant competitor notes
Tools: brave-search, fetch, Write
Pattern: Search → Extract → Synthesize → Save to vault

## Future Improvements

### High Priority (from research)
1. **ccflare/better-ccflare** — Web dashboard for cost tracking across all agents and cron jobs (github.com/tombii/better-ccflare)
2. **Dippy** — Auto-approve safe bash commands via AST parsing, reduces permission fatigue (github.com/ldayton/Dippy)
3. **TypeScript Quality Hooks** — Auto TS compilation + ESLint + Prettier on every file write (github.com/bartolli/claude-code-typescript-hooks)
4. **recall** — Full-text search across all past sessions (github.com/zippoxer/recall)

### Medium Priority
5. **Session summary hook** — Install session-summary.sh from ultimate guide
6. **GSD project setup** — Run /gsd:new-project for structured planning
7. **`.claude/rules/` directory** — Move stable rules out of CLAUDE.md for permanence
8. **Claude Squad** — Manage multiple agent instances from single terminal (github.com/smtg-ai/claude-squad)

### Low Priority
9. **Context assembler** — Modularize CLAUDE.md with @imports if project grows
10. **parry** — Prompt injection scanner for hooks (github.com/vaporif/parry)
11. **Auto-rename sessions** — Use auto-rename-session.sh for better history

---

*Last audit: 2026-03-15 | Next audit: 2026-04-15*
