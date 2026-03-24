---
type: reference
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
tags:
  - obsidian
  - knowledge-management
  - best-practices
  - workflow
---

# Obsidian Best Practices for Professional Knowledge Bases

Last Updated: 2026-03-24

## Overview

Best practices for running Obsidian as a professional consulting knowledge base. Directly relevant to how we structure the Advisor Intelligence vault at `~/obsidian-vault/` and how we might eventually template client knowledge management.

## Recommended Plugins for Professional Use

### Essential (Must-Have)

| Plugin | Purpose | Why It Matters |
|--------|---------|----------------|
| **Dataview** | Query and aggregate notes using SQL-like syntax | Most powerful plugin — creates dynamic tables, lists, and dashboards from frontmatter properties |
| **Templater** | Dynamic templates with variables, dates, conditions | Standardize note creation for clients, meetings, research |
| **Tasks** | Track TODO items across the entire vault | Query incomplete tasks by project, client, due date |
| **Homepage** | Set a custom homepage/dashboard | Create a productivity dashboard as entry point |
| **Calendar** | Calendar view linked to daily notes | Track client interactions by date |
| **Obsidian Git** | Automatic git backup of vault | Version control and backup (essential for professional use) |

### Productivity

| Plugin | Purpose |
|--------|---------|
| **Auto Note Mover** | Automatically move notes to correct folders based on tags/properties |
| **Rollover Daily Todos** | Carry incomplete daily tasks to the next day |
| **QuickAdd** | Rapid note creation with custom macros |
| **Kanban** | Visual Kanban boards for project management |
| **Excalidraw** | Visual diagrams and whiteboarding within notes |

### Data and Integration

| Plugin | Purpose |
|--------|---------|
| **Bases** (Built-in, replacing Dataview for some uses) | Native table views from properties — newer alternative to Dataview |
| **DB Folder** | Folder-based database views |
| **Periodic Notes** | Enhanced daily/weekly/monthly note system |
| **Obsidian Publish** | Publish subset of vault as documentation site |

### Our Current Vault Already Uses
- MCP integration via obsidian-rest-api for Claude Code access
- Hub-and-spoke architecture (see [[INDEX]])
- Frontmatter properties for typed notes
- [[wiki links]] throughout

## Template Systems

### Recommended Templates for Consulting

**Client Hub Template**
```markdown
---
type: client-hub
status: active
created: {{date}}
updated: {{date}}
client: "{{title}}"
aum:
tier:
crm:
---

# {{title}}

## Quick Facts
- **AUM**:
- **Location**:
- **Primary Contact**:
- **Tier**:
- **CRM**:

## Active Workflows
-

## Meeting Log
```dataview
TABLE date, summary
FROM "20-CLIENTS/{{title}}"
WHERE type = "meeting-note"
SORT date DESC
```

## Related
- [[Service-Playbook]]
```

**Meeting Note Template**
```markdown
---
type: meeting-note
status: active
created: {{date}}
updated: {{date}}
client:
attendees:
---

# Meeting: {{title}}

## Agenda
-

## Discussion Notes
-

## Action Items
- [ ]

## Follow-Up
-
```

**Research Note Template**
```markdown
---
type: reference
status: active
created: {{date}}
updated: {{date}}
domain:
tags: []
---

# {{title}}

Last Updated: {{date}}

## Overview

## Key Findings

## Sources

## Needs Further Investigation

## Related Notes
```

## Client Knowledge Base Structure

### Hub-and-Spoke Architecture (What We Use)
```
00-ADVISOR-INTELLIGENCE/  ← Sun (business core)
├── Business-Model.md
├── Service-Playbook.md
├── Tech-Stack.md
└── ...

20-CLIENTS/               ← Planets (one per client)
├── DLK/
│   ├── DLK-HUB.md       ← Client hub note
│   ├── meeting-notes/
│   ├── workflows/
│   └── deliverables/
├── ClientB/
│   ├── ClientB-HUB.md
│   └── ...
```

### Properties-Based Organization
Rather than relying solely on folders, use frontmatter properties for flexible querying:
- `type`: client-hub, meeting-note, reference, deliverable, workflow
- `status`: active, completed, archived
- `client`: client name
- `domain`: business, technical, research

This allows Dataview/Bases queries like:
```dataview
TABLE client, status, updated
FROM ""
WHERE type = "meeting-note" AND client = "DLK"
SORT updated DESC
```

### Principles
1. **One vault** — Avoid multiple vaults. Cross-linking between client and reference material is the core value
2. **Flat-ish structure** — Max 2-3 folder levels. Rely on links and properties, not deep folder hierarchies
3. **MOCs (Maps of Content)** — Use index/hub notes that link to related content rather than rigid folder trees
4. **Consistent frontmatter** — Every note gets `type`, `status`, `created`, `updated` at minimum
5. **Date format**: YYYY-MM-DD always

## Backup Strategies

### Git-Based (Primary)
- **Obsidian Git plugin**: Auto-commit on interval (every 30 min) or on file change
- Push to private GitHub/GitLab repo
- Provides full version history and rollback capability
- Our vault already lives alongside the git repo

### Cloud Storage (Secondary)
- Sync vault folder to iCloud, Dropbox, or Google Drive
- Provides continuous sync across devices
- Does NOT provide version history like git

### External Backup (Tertiary)
- Weekly tar/zip of entire vault to external storage
- Consider encrypted backups for client data

### Recommended: Git + Cloud Sync
- Git for version history and disaster recovery
- Cloud sync (iCloud/Dropbox) for mobile access and real-time sync
- Avoid syncing the `.obsidian` folder across devices if using different plugin configs

## Collaboration Approaches

### Current State
Obsidian is fundamentally a **single-user tool**. There is no real-time collaboration. Options:

### For Internal (Cri's Use)
- Single vault, git-backed, Claude Code integration via MCP
- This is the optimal setup for a solo consultant

### For Client Deliverables
- Export relevant notes as PDF or Markdown for client delivery
- Use Obsidian Publish to create a client-facing documentation site (subset of vault)
- Do NOT give clients direct vault access

### For Future Team Members
- Shared git repo with branch-per-person strategy
- Establish naming conventions and template requirements
- Use `.obsidian/` folder for shared plugin/theme config
- Document vault conventions (see [[conventions]])

### Alternative: Notion or Confluence for Client Collaboration
If real-time client collaboration becomes necessary, consider:
- Using Obsidian as the internal knowledge base
- Exporting/syncing relevant content to Notion or a shared tool for client-facing collaboration
- This maintains Obsidian's local-first privacy while enabling collaboration where needed

## Workflows for Consulting Firms

### Daily Workflow
1. Open homepage/dashboard
2. Review today's tasks (Tasks plugin or daily note)
3. Check client hub notes for active engagements
4. Take meeting notes using template
5. Update client hub with new action items
6. End of day: review incomplete tasks, plan tomorrow

### Weekly Review
1. Dataview query: all meeting notes from this week
2. Review action items across all clients
3. Update client hub statuses
4. Check for stale notes (updated > 2 weeks ago)
5. Update [[Current-Sprint]] with priorities

### Client Onboarding
1. Create client folder under `20-CLIENTS/`
2. Create hub note from template
3. Link to relevant service playbook sections
4. Create initial meeting note
5. Set up Dataview queries in hub note

### Research Workflow
1. Use brave-search or other tools to research topic
2. Create reference note in appropriate location
3. Add frontmatter properties and tags
4. Add [[wiki links]] to related notes
5. Update relevant MOC/index notes

## Needs Further Investigation
- Whether Obsidian Publish ($8/mo) is worth it for client-facing documentation
- Evaluation of Bases (built-in) vs Dataview for our use cases
- Mobile workflow optimization (iPad/iPhone)
- Whether to migrate any existing content from other tools
- Plugin performance impact as vault grows past 500+ notes

## Sources
- https://stephango.com/vault (Steph Ango's vault setup — Obsidian CEO)
- https://www.dsebastien.net/the-must-have-obsidian-plugins-for-2026/
- https://www.dsebastien.net/2022-10-19-the-must-have-obsidian-plugins/
- https://elizabethbutlermd.com/obsidian-notes/
- https://bryanhogan.com/blog/obsidian-vault
- https://forum.obsidian.md/t/professional-writers-how-do-you-organize-your-vaults/42146
- https://www.reddit.com/r/ObsidianMD/comments/18lydzh/
- https://www.reddit.com/r/ObsidianMD/comments/tt4szl/
- https://www.whytryai.com/p/claude-code-obsidian

## Related Notes
- [[conventions]]
- [[INDEX]]
- [[Current-Sprint]]
- [[vault-health]]
