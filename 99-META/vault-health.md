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
**Post-migration file count**: TBD (177 original + new axioms, principles, decisions, rules, MOCs, indexes, templates, conventions)

## Structure Verification
- [ ] Every folder has an index.md
- [ ] Every MOC links to all relevant notes
- [ ] Every note has typed frontmatter
- [ ] No orphan notes (all notes have at least one incoming link)
- [ ] No broken wiki links
- [ ] CLAUDE.md accurately describes the structure

## Known Issues
- Existing notes (177 migrated) still need frontmatter added
- Some wiki links in existing notes reference old folder paths (Obsidian resolves by filename, so this is cosmetic)

## File Count by Folder
Run: `find ~/obsidian-vault -name "*.md" -not -path '*/.git/*' | sed 's|.*/obsidian-vault/||' | cut -d'/' -f1 | sort | uniq -c | sort -rn`
