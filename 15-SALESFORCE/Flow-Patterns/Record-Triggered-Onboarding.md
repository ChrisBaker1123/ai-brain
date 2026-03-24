---
type: reference
title: "Salesforce Flow Pattern: Record-Triggered Onboarding"
status: active
created: 2026-03-24
---

# Flow Pattern: Record-Triggered Onboarding

> Reusable pattern. First implemented for DLK WF2.

## Pattern

When a new Contact is created with a specific type, auto-generate a predefined set of Tasks assigned to appropriate team members.

## Flow Design

```
TRIGGER: Record-Triggered Flow
  Object: Contact
  When: After save (new record)
  Condition: Type = "Prospect" OR Type = "New Client"

DECISION: Check Contact Type
  Path 1: "Prospect" → Create prospect task set
  Path 2: "New Client" → Create full onboarding task set

ACTION: Create Task Records
  For each task in the template:
    - Subject: "[Task Name] — {Contact.Name}"
    - Assigned To: [Role-based lookup]
    - Due Date: Contact.CreatedDate + [offset days]
    - Related To: Contact record
    - Priority: [High/Normal based on task]
    - Status: "Not Started"

ACTION: Update Contact
  - Onboarding_Status__c = "In Progress"
  - Onboarding_Start_Date__c = TODAY()
  - Pipeline_Stage__c = "Onboarding"
```

## Task Template (DLK-specific)

| Task | Assigned To | Due Offset | Priority |
|------|------------|-----------|----------|
| Send disclosure documents | Mark/Compliance | +1 day | High |
| Set up in billing system | Operations | +3 days | High |
| Assign to investment model | Brian | +3 days | Normal |
| Enter account data for trading | Brian | +5 days | Normal |
| Add to newsletter distribution | Admin | +3 days | Normal |
| Schedule introductory review | Mark | +7 days | High |
| 30-day check-in reminder | Mark | +30 days | Normal |
| 60-day check-in reminder | Mark | +60 days | Normal |
| 90-day review reminder | Mark | +90 days | Normal |

## Considerations

- Flow runs **after save** (not before) to ensure Contact ID exists for task assignment
- Use **Assignment Rules** or a custom field for dynamic owner assignment
- Consider a **Subflow** for the task creation loop (reusable across clients)
- Test with a sample Contact before deploying to production
- Set up **error handling** in Flow for missing required fields

## Adapting for Other Clients

Replace the task template with the client's specific onboarding steps. The Flow structure remains the same — only the tasks and assignments change.

---

## Related

- [[15-SALESFORCE/FSC-Features|Salesforce Features]]
- [[20-CLIENTS/DLK/Workflows/WF2-Client-Onboarding/Spec|DLK WF2 Spec]]
