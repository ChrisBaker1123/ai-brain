---
type: reference
title: "Vault Health"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: business
---

# Vault Health

## Last Restructure
**Date**: 2026-03-16
**Pre-migration file count**: 177 markdown files
**Post-migration file count**: 235 markdown files (177 original + 58 new)

## Structure Verification
- [x] Every content folder has an index.md (10 indexes)
- [x] 7 MOCs link to all relevant notes
- [x] 234/235 notes have typed frontmatter (CLAUDE.md excluded by design)
- [x] All old folders removed (00-INDEX through 13-PERSONAL)
- [x] CLAUDE.md accurately describes the structure
- [ ] Orphan note check (run manually)
- [ ] Broken wiki link check (run manually)

## File Count by Folder (2026-03-16)
| Folder | Files | Type |
|--------|-------|------|
| 05-PROJECTS | 61 | project/reference |
| 08-REFERENCE | 42 | reference |
| 10-DRAFTS | 18 | draft |
| 11-LOGS | 17 | log |
| 99-META | 14 | reference |
| 06-AREAS | 13 | plan/reference |
| 12-PERSONAL | 12 | personal |
| 07-CONTACTS | 11 | contact/reference |
| 01-AXIOMS | 9 | axiom |
| 00-MAPS | 9 | moc |
| 09-PLANS | 7 | plan |
| 04-RULES | 7 | rule |
| 03-DECISIONS | 7 | decision |
| 02-PRINCIPLES | 7 | principle |
| CLAUDE.md | 1 | agent interface |
| **Total** | **235** | |

## Refresh Command
```bash
find ~/obsidian-vault -name "*.md" -not -path '*/.git/*' | sed 's|.*/obsidian-vault/||' | cut -d'/' -f1 | sort | uniq -c | sort -rn
```
