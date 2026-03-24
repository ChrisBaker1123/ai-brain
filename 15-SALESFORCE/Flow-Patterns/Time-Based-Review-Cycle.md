---
type: reference
title: "Salesforce Flow Pattern: Time-Based Review Cycle"
status: active
created: 2026-03-24
---

# Flow Pattern: Time-Based Review Cycle

> Reusable pattern. First implemented for DLK WF3.

## Pattern

Scheduled Flow runs daily, checking for clients approaching their next review date. Creates tasks and draft emails at defined intervals (60 days, 30 days).

## Flow Design

```
TRIGGER: Schedule-Triggered Flow
  Frequency: Daily at 6:00 AM PT
  Object: Contact (query within flow)

STEP 1: Get Records — 60-Day Contacts
  Query: Contact WHERE
    Next_Review_Date__c = TODAY() + 60
    AND Review_Status__c != "Email Sent"
    AND Review_Status__c != "Confirmed"
    AND Review_Status__c != "Completed"

  FOR EACH Contact:
    ACTION: Create Task
      Subject: "Draft review email — {Contact.Name}"
      Assigned To: Contact.Owner (Mark or Tom)
      Due Date: TODAY() + 7
      Priority: Normal
      Description: [Include email template with merge fields]

    ACTION: Update Contact
      Review_Status__c = "Email Sent"

STEP 2: Get Records — 30-Day Contacts (Escalation)
  Query: Contact WHERE
    Next_Review_Date__c = TODAY() + 30
    AND Review_Status__c = "Email Sent"
    (client hasn't confirmed after 30 days)

  FOR EACH Contact:
    ACTION: Create Task
      Subject: "⚠️ Follow up: {Contact.Name} — review in 30 days, no response"
      Assigned To: Contact.Owner
      Due Date: TODAY() + 3
      Priority: High

STEP 3: Get Records — Overdue Reviews
  Query: Contact WHERE
    Next_Review_Date__c < TODAY()
    AND Review_Status__c != "Completed"

  FOR EACH Contact:
    ACTION: Create Task
      Subject: "🔴 OVERDUE: {Contact.Name} review was due {Next_Review_Date}"
      Assigned To: Contact.Owner
      Due Date: TODAY()
      Priority: High
```

## Post-Meeting Update (Manual + AI-Assisted)

After a review meeting is completed:
1. Advisor updates Contact record:
   - Last_Review_Date__c = meeting date
   - Next_Review_Date__c auto-calculates (+ 90 days)
   - Review_Status__c = "Completed"
   - Review_Notes__c = meeting notes (AI-assisted summarization)
2. Flow creates follow-up tasks from meeting action items
3. AI drafts recap email to client (to advisor's drafts)

## Dashboard Component

**Lightning Report Chart** on homepage:

| Section | Content |
|---------|---------|
| **Due in 30 days** | List of clients with reviews in next 30 days, status indicator |
| **Due in 30-60 days** | List with draft email status |
| **Due in 60-90 days** | Planning horizon |
| **Overdue** | Red flag, immediate attention |

## Custom Fields Required

| Field | Type | Object | Default |
|-------|------|--------|---------|
| Last_Review_Date__c | Date | Contact | — |
| Next_Review_Date__c | Formula (Date) | Contact | Last_Review_Date + 90 |
| Review_Status__c | Picklist | Contact | "Scheduled" |
| Review_Notes__c | Long Text Area | Contact | — |
| Review_Interval__c | Number | Contact | 90 (days) |
| Outstanding_Items__c | Long Text Area | Contact | — |

## Considerations

- Scheduled Flows have execution limits (250K records per 24 hours) — not an issue for ~470 clients
- Use **Platform Events** if real-time notifications are needed
- Consider **Email Alerts** in addition to Tasks for time-sensitive follow-ups
- Test the 60/30/overdue logic with sample dates before deploying

---

## Related

- [[15-SALESFORCE/FSC-Features|Salesforce Features]]
- [[20-CLIENTS/DLK/Workflows/WF3-Review-Cycle/Spec|DLK WF3 Spec]]
