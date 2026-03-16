---
type: reference
title: "Vault Conventions"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: business
---

# Vault Conventions

The rules that govern this knowledge system. Claude Code and Cri both follow these.

## Frontmatter Schema

Every note MUST have YAML frontmatter. The schema below is the contract.

### Required Fields (every note)

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

### Type-Specific Fields

#### Axioms (01-AXIOMS/)
```yaml
confidence: proven | strong | developing | speculative
statement: "One-line distillation of the belief"
```

#### Principles (02-PRINCIPLES/)
```yaml
derived_from:
  - "[[axiom-note-name]]"
```

#### Decisions (03-DECISIONS/)
```yaml
decided: YYYY-MM-DD
rationale: "One-line reason"
revisit: YYYY-MM-DD   # Optional: when to reconsider
derived_from:
  - "[[principle-or-axiom-name]]"
```

#### Rules (04-RULES/)
```yaml
enforcement: strict | soft
derived_from:
  - "[[decision-or-principle-name]]"
```

#### Contacts (07-CONTACTS/)
```yaml
role: client | prospect | mentor | family | colleague | referral
company: "Company name"
relationship: active | dormant | potential
priority: high | medium | low
```

#### Reference Notes (08-REFERENCE/)
```yaml
source: "URL or source description"
reliability: high | medium | low | unverified
```

#### Drafts (10-DRAFTS/)
```yaml
target_platform: linkedin | blog | email | outreach
publish_status: idea | drafting | review | published
```

## Type Hierarchy

The core reasoning layer. Traverse upward to understand WHY something exists:

```
axiom (foundational truth)
  → principle (derived behavior)
    → decision (choice with rationale)
      → rule (hard constraint)
```

`derived_from` links make this traversable. When evaluating a decision, check which principles informed it. When evaluating a principle, check which axioms ground it.

## Naming Conventions

- **Filenames**: kebab-case (`gap-filler-positioning.md`)
- **Decision files**: `YYYY-MM-description.md` (`2026-03-pivot-to-gap-filler.md`)
- **Contact files**: `Contact-LastName-FirstName.md` or `Client-Name.md`
- **Component files**: `Component-Name.md`
- **Page files**: `Page-Name.md`
- **Monitor logs**: `monitor-YYYY-MM-DD-HHMM.md`
- **Session logs**: `YYYY-MM-DD-description.md`
- **Draft files**: `YYYY-MM-DD.md` (daily batches) or `topic-name.md` (topical)

## Wiki Links

- Use `[[note-name]]` without folder paths — Obsidian resolves by filename
- For display text: `[[note-name|Display Text]]`
- Links survive file moves because they resolve by filename
- Always add links to related notes at the bottom of every note

## Folder Structure

| Folder | Type | Purpose |
|--------|------|---------|
| 00-MAPS | moc | Entry points by theme |
| 01-AXIOMS | axiom | Foundational beliefs |
| 02-PRINCIPLES | principle | Derived behaviors |
| 03-DECISIONS | decision | Choices with rationale |
| 04-RULES | rule | Hard constraints |
| 05-PROJECTS | project | Active projects |
| 06-AREAS | reference/project | Ongoing responsibilities |
| 07-CONTACTS | contact | People |
| 08-REFERENCE | reference | Research and market data |
| 09-PLANS | plan | Roadmaps and strategies |
| 10-DRAFTS | draft | Content drafts |
| 11-LOGS | log | Time-based records |
| 12-PERSONAL | personal | Identity and biography |
| 99-META | reference | Vault management |

## When Creating a New Note

1. Use the correct template from `99-META/templates/`
2. Fill ALL required frontmatter fields
3. Add `[[wiki links]]` to related notes
4. Update the parent folder's `index.md`
5. Update the relevant MOC(s) in `00-MAPS/`
6. If it's a decision, link `derived_from` to the principle/axiom
7. If it changes another note, update that note's `updated` field

## When Updating an Existing Note

1. Update the `updated` field in frontmatter
2. If the update changes a decision, create a NEW decision note and archive the old one
3. Update relevant MOCs and indexes if the change is structural

## Tags

Use sparingly. The `domain` frontmatter field handles primary categorization. Tags are for cross-cutting concerns:
- `#confidential` — vault-only content
- `#private` — personal/family information
- `#urgent` — time-sensitive items

## Status Lifecycle

```
draft → active → deprecated → archived
                → speculative (for uncertain/exploratory content)
```

## Archive Policy

- Don't delete notes. Change status to `archived`.
- Archived notes stay in their current folder.
- If a decision is superseded, archive the old one and create a new one.
