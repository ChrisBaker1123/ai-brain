---
type: decision
title: "Use 8 workflow categories for templates"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: product
decided: 2026-03-14
rationale: "Categories should reflect what advisors DO during their day, not financial planning functions"
derived_from:
  - "[[workflow-not-function]]"
  - "[[gap-filler-positioning]]"
---

## Decision
Templates organized into 8 workflow-based categories: meeting_prep, follow_up_crm, client_emails, client_education, prospecting_growth, content_creation, new_client_onboarding, practice_operations.

## Context
Original 11 categories organized by planning function (estate planning, tax planning, etc.) signaled we were trying to replace dedicated software.

## Rationale
Workflow categories match advisor daily reality. Meeting prep and follow-ups are daily. Client emails are constant. These are the tasks no existing software handles. Organizing by workflow signals "we understand your day."

## Implications
- prompts-data.json restructured
- dashboard-shell.tsx sidebar updated
- Landing page category showcase updated
- URL slugs use hyphens (meeting-prep) while data uses underscores (meeting_prep) via toSlug()

## Related
- [[Product-Strategy-Pivot]]
- [[Architecture]]
- [[Overview]]
