---
type: spec
title: "WF3: Client Review Cycle Automation"
status: planning
created: 2026-03-24
client: DLK
owner: Mark Halby
---

# WF3: Client Review Cycle Automation

> Automate the 90-day client review scheduling, email outreach, and post-meeting documentation.

## Problem

Mark manually tracks review dates, writes individual emails to every client, and manages follow-ups. With a 1:78 client ratio, reviews pile up and some get missed. He wants to see upcoming reviews on his homepage and have the system handle the repetitive parts.

## Requirements (from transcript)

### Review Scheduling
- Salesforce tracks last review date and next review date for every client
- Homepage shows: upcoming reviews for next 90 days, which are in next 30 days
- Ability to trigger review emails from the dashboard

### Automated Outreach
1. **At 60 days before next review**: Auto-generate draft email
   - "It's time for your periodic review"
   - Include client name, any outstanding items from last meeting, personalized touches
   - Goes to Mark's drafts — **not sent automatically**
2. **At 30 days before review**: If client hasn't responded, create task on Mark's homepage
   - Escalation: "Client X has not responded to review request"

### Pre-Meeting Brief
- Generate one-page client brief pulling from Salesforce data:
  - Last meeting notes
  - Account summary (AUM, model, recent activity)
  - Life events (birthdays, milestones, family changes)
  - Outstanding tasks from last meeting
  - Upcoming milestones (kids' graduations, retirements)
  - Suggested talking points

### Post-Meeting
- AI processes meeting notes into structured CRM update
- Creates follow-up tasks from meeting action items
- Drafts recap email to client
- Updates Last_Review_Date, calculates Next_Review_Date

## Technical Approach

### Salesforce Components

#### Custom Fields (on Contact or Account)
| Field | Type | Purpose |
|-------|------|---------|
| Last_Review_Date__c | Date | Date of last completed review |
| Next_Review_Date__c | Date/Formula | Last_Review_Date + 90 days (or custom interval) |
| Review_Status__c | Picklist | Scheduled / Email Sent / Confirmed / Completed / Overdue |
| Review_Notes__c | Long Text | Notes from last review |
| Outstanding_Items__c | Long Text | Open items from last review |

#### Scheduled Flow (Time-Based)
- **Trigger**: Daily scheduled flow
- **Logic**:
  1. Query all Contacts where Next_Review_Date is 60 days from today AND Review_Status != "Email Sent"
  2. For each: Create Task "Draft review email for [Client Name]" assigned to Mark
  3. (If email templates available) Generate draft email using template with merge fields
  4. Update Review_Status to "Email Sent"

- **30-day escalation**:
  1. Query Contacts where Next_Review_Date is 30 days from today AND Review_Status = "Email Sent" (not confirmed)
  2. Create high-priority Task "Follow up: [Client] has not responded to review request"

#### Homepage Dashboard
- **Report**: Upcoming Reviews (next 90 days)
  - Grouped by: Next 30 days / 30-60 days / 60-90 days
  - Columns: Client name, next review date, status, last review date
  - Color coding: overdue (red), due in 30 days (yellow), scheduled (green)

### Email Templates

#### Review Request (60-day)
```
Subject: Time for Your Periodic Review — {{Client_Name}}

Hi {{First_Name}},

I hope you're doing well. It's been about 90 days since our last review,
and I'd like to schedule some time to go over your portfolio and any
updates in your financial picture.

{{#if Outstanding_Items}}
From our last conversation, we had a few items to follow up on:
{{Outstanding_Items}}
{{/if}}

Would any of the following weeks work for you? [suggest 2-3 date ranges]

Looking forward to connecting.

Best,
Mark Halby, CFP®, AIF®
DLK Investment Management
(858) 433-3204
```

#### Follow-Up (30-day escalation)
```
Subject: Following Up — Review Scheduling

Hi {{First_Name}},

I wanted to circle back on scheduling your periodic review. I know
things get busy — I'm flexible on timing and happy to do a phone
call if that's easier than meeting in person.

Just let me know what works best.

Best,
Mark
```

### Meeting Notes Pipeline

For in-person meetings (Mark's specific ask):
1. **Recording**: Otter.ai on phone or tablet → auto-transcription
2. **Processing**: AI summarizes transcript into structured notes
3. **CRM Update**: Structured notes → Salesforce Contact record
4. **Follow-up**: AI extracts action items → creates Tasks
5. **Recap email**: AI drafts recap email → Mark's drafts

## Implementation Plan

### Requires from DLK
- [ ] Salesforce access (same as WF2)
- [ ] Mark's review email templates (or approval to create new ones)
- [ ] Current review tracking method (so we can migrate data)
- [ ] List of client review intervals (all 90 days, or varies?)
- [ ] Decision on meeting recording tool

### Build Steps
1. Create custom fields (review dates, status, notes)
2. Build scheduled Flow for 60-day and 30-day triggers
3. Create email templates
4. Build review dashboard on homepage
5. (Phase 2) Build pre-meeting brief generator
6. (Phase 2) Build post-meeting notes pipeline
7. Demo to Mark and Tom
8. Iterate based on feedback
9. Deploy to production
10. Train team

## Open Questions

1. Are all client reviews on 90-day cycles, or do some clients have different intervals?
2. Does Mark want the draft email in Salesforce drafts or Outlook drafts?
3. How does Mark currently track meeting notes? (Written? Digital? None?)
4. Is Tom's review process identical to Mark's?
5. Would Don want to see a compliance report of overdue reviews?
6. Budget for meeting transcription tool? (Otter.ai ~$100/year)

## Success Criteria

Mark considers this successful if:
- He can see on his homepage: all upcoming reviews, grouped by urgency
- Draft emails are generated automatically at 60 days — he just reviews and sends
- Overdue reviews are flagged automatically at 30 days
- Nothing gets missed — the system tracks everything

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/People/Mark-Halby|Mark Halby]]
- [[20-CLIENTS/DLK/Workflows/WF2-Client-Onboarding/Spec|WF2: Client Onboarding]] — Shares Salesforce infrastructure
- [[15-SALESFORCE/Flow-Patterns/Time-Based-Review-Cycle|Time-Based Review Cycle Pattern]]
