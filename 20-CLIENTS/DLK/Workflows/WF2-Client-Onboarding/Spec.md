---
type: spec
title: "WF2: New Client Onboarding Sequence"
status: planning
created: 2026-03-24
client: DLK
owner: Mark Halby
---

# WF2: New Client Onboarding Sequence in Salesforce

> When a new prospect/client is created, automatically generate all required tasks and track pipeline.

## Problem

Mark currently creates all onboarding tasks manually for every new prospect/client. There's no standardized checklist, no pipeline visibility, and tasks fall through the cracks. He wants to see "where are we in the process? What's already been done and what still needs to be done?"

## Requirements (from transcript)

### Trigger
New Contact created in Salesforce with Type = "Prospect" or "New Client"

### Auto-Generated Tasks

| # | Task | Assigned To | Due |
|---|------|------------|-----|
| 1 | Send disclosure documents | Mark (or compliance) | Day 1 |
| 2 | Set up in billing system | Operations | Day 3 |
| 3 | Assign to investment model | Brian | Day 3 |
| 4 | Enter account data for trading | Brian | Day 5 |
| 5 | Add to newsletter distribution (Mailchimp) | Admin | Day 3 |
| 6 | Schedule introductory review meeting | Mark | Day 7 |
| 7 | Set 30-day calendar reminder | Mark | Day 30 |
| 8 | Set 60-day calendar reminder | Mark | Day 60 |
| 9 | Set 90-day calendar reminder | Mark | Day 90 |
| 10 | Draft welcome email (to Mark's drafts, not auto-sent) | AI | Day 1 |

### Pipeline Dashboard
- Homepage component showing:
  - All active prospects/clients in onboarding
  - Each person's stage in the pipeline
  - Tasks completed vs outstanding per person
  - Overall onboarding health (on track / delayed / at risk)

## Technical Approach

### Option A: Salesforce Record-Triggered Flow (Recommended)
- **Trigger**: After Contact is created, when Type = "Prospect" OR Type = "New Client"
- **Actions**: Create Task records for each step, assigned to appropriate users
- **Conditions**: Different task sets based on Contact Type (prospect = fewer tasks, new client = full list)
- **Requirements**: Professional Edition or higher, Flow Builder access

### Option B: Action Plan Templates (if available)
- Salesforce Action Plans = predefined task templates that attach to records
- Available in Financial Services Cloud or via add-on
- More flexible for managing templates across different client types
- **Requirements**: Financial Services Cloud or Enterprise + add-on

### Option C: Apex Trigger (fallback)
- If Flow limitations are hit (complex logic, external callouts)
- Requires developer console access
- More flexible but harder for Mark to modify

### Dashboard Approach
- **Lightning App Page**: Custom homepage component
- **Report-based**: Report on Tasks filtered by onboarding, grouped by Contact
- **List View**: Tasks with filters for onboarding type
- **Kanban**: If Opportunities are used for pipeline, Kanban view works natively

## Custom Fields Needed

| Object | Field | Type | Purpose |
|--------|-------|------|---------|
| Contact | Onboarding_Status__c | Picklist | Not Started / In Progress / Complete |
| Contact | Onboarding_Start_Date__c | Date | When onboarding began |
| Contact | Pipeline_Stage__c | Picklist | Prospect / Onboarding / Active Client / Churned |
| Contact | Investment_Model__c | Picklist | Which model to assign (Brian needs this) |
| Contact | Last_Review_Date__c | Date | For WF3 |
| Contact | Next_Review_Date__c | Date | For WF3 |

## Implementation Plan

### Requires from DLK
- [ ] Salesforce edition confirmation
- [ ] Dedicated admin user account for Cri
- [ ] List of all task owners (who handles what)
- [ ] Approval of task list and due dates
- [ ] Approval of custom fields

### Build Steps
1. Create custom fields on Contact object
2. Build Record-Triggered Flow
3. Test with sample Contact
4. Build homepage report/dashboard component
5. Demo to Mark
6. Iterate based on feedback
7. Deploy to production
8. Train Mark and team

## Open Questions

1. What Salesforce edition is DLK on?
2. Are they using Contacts, Accounts, or both for clients?
3. Do they have existing custom fields we should preserve?
4. Who is the task owner for each step? (confirm exact assignments)
5. Does Mark want different task lists for Prospect vs New Client?
6. Is there a separate billing system, or is billing tracked in Salesforce?

## Success Criteria

Mark considers this successful if:
- New prospect creation triggers automatic task list (zero manual creation)
- He can see on his homepage: all prospects, where they are, what's done/outstanding
- Tasks are assigned to the right people automatically
- Nothing falls through the cracks

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/People/Mark-Halby|Mark Halby]]
- [[20-CLIENTS/DLK/Tech-Stack/Salesforce-Audit|Salesforce Audit]]
- [[15-SALESFORCE/Flow-Patterns/Record-Triggered-Onboarding|Record-Triggered Onboarding Pattern]]
