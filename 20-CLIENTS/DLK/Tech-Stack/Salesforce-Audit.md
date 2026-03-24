---
type: document
title: "DLK Salesforce Audit"
status: pending
created: 2026-03-24
client: DLK
---

# DLK Salesforce Audit

> **Status**: Pending — requires Salesforce access. Complete during Week 1.

## Pre-Audit Questions (ask Mark or Don)

- [ ] What Salesforce edition are you on? (Essentials / Professional / Enterprise / Unlimited)
- [ ] How many licensed users?
- [ ] Do you have Financial Services Cloud?
- [ ] Who is your Salesforce admin? (or is there one?)
- [ ] Any third-party apps installed? (Practifi, XLR8, Salentica?)
- [ ] Is email synced with Salesforce?
- [ ] Is calendar synced?
- [ ] What reports/dashboards do you currently use?

## Audit Checklist (complete once access granted)

### Edition & Licensing
- [ ] Edition confirmed: ___________
- [ ] Licensed users: ___
- [ ] API access: Yes / No
- [ ] Flow Builder available: Yes / No
- [ ] Custom objects allowed: Yes / No

### Current Object Usage
- [ ] Contacts: ___
- [ ] Accounts: ___
- [ ] Opportunities: ___
- [ ] Tasks: ___
- [ ] Events: ___
- [ ] Custom Objects: ___

### Custom Fields
- [ ] Contact custom fields: ___
- [ ] Account custom fields: ___
- [ ] Review date fields exist? ___
- [ ] Client type fields? ___

### Existing Automations
- [ ] Flows: ___
- [ ] Process Builders: ___
- [ ] Workflow Rules: ___
- [ ] Apex: ___

### Homepage
- [ ] Default or customized: ___
- [ ] Components currently on homepage: ___

### Integrations
- [ ] Email sync: ___
- [ ] Calendar sync: ___
- [ ] Any custodian integration: ___
- [ ] Mailchimp connection: ___

## Known Pain Points (from transcript)

1. Mark wants auto-task generation on new prospect creation
2. Mark wants pipeline visibility on his homepage
3. Mark wants review cycle tracking (last review, next review, upcoming)
4. No existing automations — everything is manual
5. Using primarily as a contact database, not a workflow engine

## Recommendations (pre-audit hypotheses)

1. **Record-Triggered Flow**: When Contact.Type = "Prospect" or "New Client" → auto-create task list
2. **Lightning Homepage**: Custom component showing pipeline (prospects by stage, tasks due)
3. **Custom fields**: Add Review_Last_Date, Review_Next_Date, Client_Type, Pipeline_Stage
4. **Time-Based Flow**: At Review_Next_Date - 60 days → create draft email task
5. **Reports**: Build a review cycle dashboard, pipeline report, onboarding status report

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Tech-Stack/Current-Stack|Current Stack]]
- [[15-SALESFORCE/FSC-Features|Salesforce FSC Reference]]
