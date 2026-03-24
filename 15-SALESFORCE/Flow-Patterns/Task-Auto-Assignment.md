---
type: reference
title: "Salesforce Flow Pattern: Task Auto-Assignment"
status: active
created: 2026-03-24
---

# Flow Pattern: Task Auto-Assignment

> Reusable pattern for assigning tasks to the right team member based on role or task type.

## Pattern

When auto-generating tasks, assign to the correct person based on task category rather than hardcoding user IDs.

## Approach: Custom Metadata or Custom Setting

Create a mapping table:

| Task Category | Assigned To (Role) | Default User |
|--------------|-------------------|-------------|
| Compliance/Disclosures | CCO | Don Dempster |
| Billing/Operations | Operations | [TBD] |
| Trading/Models | Trading | Brian Johnson |
| Client Communication | Advisor (Contact Owner) | Mark/Tom |
| Administrative | Admin | [TBD] |
| Calendar/Scheduling | Advisor (Contact Owner) | Mark/Tom |

## Flow Implementation

```
SUBFLOW: Assign_Task_Owner
  Input: Task_Category (text)

  DECISION: Route by Category
    "Compliance" → Get User where Role = CCO
    "Trading" → Get User where Name = "Brian Johnson"
    "Operations" → Get User where Role = Operations
    "Advisor" → Use Contact.OwnerId (the assigned advisor)
    "Admin" → Get User where Role = Admin

  Output: Assigned_User_Id
```

## Why Not Hardcode?

- User IDs change if someone leaves
- Multiple clients may have different team structures
- Easy to update the mapping table without modifying Flows
- Scales across future clients

---

## Related

- [[15-SALESFORCE/Flow-Patterns/Record-Triggered-Onboarding|Onboarding Flow]]
- [[15-SALESFORCE/FSC-Features|Salesforce Features]]
