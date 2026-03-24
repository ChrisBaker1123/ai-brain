# CLAUDE.md — Agent Interface for Cri's Knowledge Vault

## Who You're Working For

Christopher "Cri" Baker. 20 years old, SDSU Fowler Scholar (Class of 2028), finance major, San Diego native. Son of a 30-year Morgan Stanley financial advisor. Bilingual in technology and finance. Building Advisor Intelligence as Phase 1 of a career plan. Read [[Me]] for full context when creating content, outreach, or anything that represents his voice.

**Phone**: (619) 851-2215 | **Site**: https://www.advisorintelligence.app
**Core identity**: trustworthy, friendly, intelligent, professional. Same person on Instagram as in a meeting with a $500M advisor.

## Vault Architecture

This vault uses **typed frontmatter**. Every note has a `type` field in YAML. The type hierarchy is the reasoning layer:

```
axiom (foundational truth Cri accepts)
  → principle (behavior derived from axioms)
    → decision (choice made with rationale)
      → rule (hard constraint)
```

`derived_from` links make this traversable. When making decisions or generating content, **traverse the hierarchy**: check relevant axioms and principles first. This is how the vault answers "what should I do?" not just "what do I know?"

Supporting types: `reference`, `project`, `log`, `draft`, `personal`, `plan`, `contact`, `moc`.

## How to Navigate

1. **Start with the relevant MOC** in `00-MAPS/`
2. Read the MOC to understand the topic landscape
3. Read only the specific notes you need
4. **NEVER read the entire vault.** Use MOCs and indexes.

### Quick Access by Task

| Task | Start Here |
|------|-----------|
| Any task | [[Current-Sprint]] — what to work on |
| Content creation | [[MOC-Marketing]] → [[Brand-Voice]] → [[Advisor-Language-Bank]] |
| Client/prospect work | [[MOC-Client-Pipeline]] → relevant contact notes |
| Feature work | [[MOC-Advisor-Intelligence]] → [[Architecture]] |
| Marketing | [[MOC-Marketing]] → [[Marketing-Strategy]] |
| Research | [[MOC-Research]] → [[Research-Digest]] |
| Personal/brand | [[MOC-Personal]] → [[Me]] → [[Brand-Identity]] |
| Product decisions | [[MOC-Product]] → [[Product-Strategy-Pivot]] |
| Understanding beliefs | [[01-AXIOMS/index]] → specific axiom |

## Folder Structure

```
obsidian-vault/
├── CLAUDE.md              # This file — read first every session
├── 00-MAPS/               # Maps of Content (entry points by theme)
│   ├── INDEX.md           # Master vault map
│   ├── MOC-Advisor-Intelligence.md
│   ├── MOC-Client-Pipeline.md
│   ├── MOC-Product.md
│   ├── MOC-Marketing.md
│   ├── MOC-Personal.md
│   ├── MOC-Research.md
│   ├── MOC-Education.md
│   └── CHANGELOG.md
├── 01-AXIOMS/             # Foundational beliefs (8 notes)
├── 02-PRINCIPLES/         # Derived behaviors (6 notes)
├── 03-DECISIONS/          # Choices with rationale (6 notes)
├── 04-RULES/              # Hard constraints (6 notes)
├── 05-PROJECTS/           # Active projects
│   ├── advisor-intelligence/  # Main product
│   │   ├── pages/         # 28 route docs
│   │   ├── components/    # 17 component docs
│   │   └── database/      # 5 schema/auth/API docs
│   ├── dlk-engagement/    # Priority prospect
│   └── White-Label-Platform.md
├── 06-AREAS/              # Ongoing areas (marketing, content, investing)
├── 07-CONTACTS/           # People (clients, prospects, mentors, family)
├── 08-REFERENCE/          # Research, competitors, market data
│   ├── competitors/       # 13 competitor analyses
│   ├── market-research/   # Advisor insights, industry intel
│   ├── san-diego-rias/    # Local RIA map, prospects
│   ├── seo-content/       # SEO/AEO research
│   ├── linkedin/          # LinkedIn research
│   ├── strategy/          # Product strategy research
│   └── email/             # Email research
├── 09-PLANS/              # Roadmaps, sprints, master plan
├── 10-DRAFTS/             # Content drafts (linkedin, blog, email, outreach)
├── 11-LOGS/               # Session logs, monitor logs, playbooks
├── 12-PERSONAL/           # Identity, family, values, biography
└── 99-META/               # Templates, conventions, vault management
    ├── templates/         # 12 note templates (one per type)
    └── conventions.md     # Full frontmatter schema and rules
```

## Frontmatter Schema (Quick Reference)

Every note MUST have:
```yaml
---
type: axiom | principle | decision | rule | reference | project | log | draft | personal | plan | contact | moc
title: "Human-readable title"
status: active | archived | draft | deprecated | speculative
created: YYYY-MM-DD
updated: YYYY-MM-DD
domain: business | product | marketing | personal | investing | education | outreach
---
```

See [[conventions]] for type-specific fields and full schema.

## How to Create New Notes

1. Use the correct template from `99-META/templates/`
2. Fill ALL required frontmatter fields
3. Add `[[wiki links]]` to related notes
4. Update the parent folder's `index.md`
5. Update the relevant MOC(s) in `00-MAPS/`
6. If it's a decision, link `derived_from` to the axiom/principle it follows from

## How to Update Existing Notes

1. Always update the `updated` field in frontmatter
2. If the update supersedes a decision, create a new decision note and archive the old one
3. Update relevant MOCs and indexes if the change is structural

## Conventions

- **Filenames**: kebab-case (`gap-filler-positioning.md`)
- **Wiki links**: `[[note-name]]` without folder paths (Obsidian resolves them)
- **Tags**: use sparingly — frontmatter `domain` field handles categorization
- **Dates**: YYYY-MM-DD format
- **Status**: active / archived / draft / deprecated / speculative

## Content Voice

When creating content that represents Cri:
- Trustworthy, friendly, intelligent, professional
- Same voice on Instagram as in a meeting with a $500M advisor
- "Compliance-aware, not compliance-approved"
- "Templates" not "prompts," "AI Coach" not "chatbot"
- Microsoft Copilot is the primary AI tool reference
- Read [[Brand-Voice]] and [[Lil-Chris]] for full brand context

## Confidential Information

- The 3-phase business plan (AI coaching → AI architecture → financial advisor) — vault only
- Personal/family details inform content but never appear in public output
- Investment positions and thesis are private
- Client details (AUM, specific strategies) require permission to reference

## Key Rules (Non-Negotiable)

- **Never fabricate** user counts, testimonials, or social proof
- **Never position** as replacement for eMoney, Holistiplan, Riskalyze, Orion
- **Never claim** compliance approval — always "compliance-aware"
- **Never use** "guaranteed," "proven," "risk-free," "#1," "best"
- **Never leak** the 3-phase plan or family details into public content
- See [[04-RULES/index]] for the full list

## Session Journaling (Non-Negotiable)

At the END of every Claude Code session, before the final git commit:
1. Create or update today's journal entry in `30-SESSION-JOURNAL/YYYY-MM-DD/`
2. Log what was done, what was learned, what's still open
3. Update `30-SESSION-JOURNAL/LEARNINGS.md` with any new insights
4. Update `30-SESSION-JOURNAL/INDEX.md` with the new entry
5. Include the journal files in the git commit

Every session gets documented. No exceptions. This is how we build institutional memory.
