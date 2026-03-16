---
title: "Template Pivot Implementation Plan"
type: roadmap
date: 2026-03-14
status: completed
tags: [implementation, pivot, templates]
---

# Template Pivot Implementation Plan

Based on [[Product-Strategy-Pivot]] research findings. Transforms 61 templates (11 categories) → 68 templates (8 workflow categories).

## Summary of Changes

### Categories: 11 → 8
| # | New Category | ID | Templates |
|---|-------------|-----|-----------|
| 1 | Meeting Prep | meeting_prep | 9 |
| 2 | Follow-Up & CRM | follow_up_crm | 5 |
| 3 | Client Emails | client_emails | 13 |
| 4 | Client Education | client_education | 14 |
| 5 | Prospecting & Growth | prospecting_growth | 9 |
| 6 | Content Creation | content_creation | 6 |
| 7 | New Client Onboarding | new_client_onboarding | 5 |
| 8 | Practice Operations | practice_operations | 7 |

### Templates: 61 → 68
- **KEEP** (30): Retain as-is, reassign to new categories
- **RETHINK** (18): Rename, reframe prompts, reassign categories
- **REMOVE** (13): Archive — overlap with regulated advisor software
- **NEW** (20): Fill genuine workflow gaps

### Removed Templates (13)
1.3, 9.1, 9.2, 10.1, 10.2, 10.4, 12.1, 12.2, 12.3, 12.5, 12.6, 12.7, 12.8

### Eliminated Categories (3)
- Tax Planning → templates moved to Client Education + Client Emails
- Retirement Planning → templates moved to Client Education
- Deep Analysis → entire category removed (7/8 redundant)

## Implementation Steps

### Step 1: Transform prompts-data.json
Python script to restructure the 531KB JSON:
- New 8-category definitions
- Remove 13 templates
- Move + rename 18 RETHINK templates
- Reassign 30 KEEP templates to new categories
- Add 20 NEW templates with full prompt content

### Step 2: Update prompts.ts
- New DESCRIPTIONS for all 68 templates
- New RELATED_CATEGORIES for 8 categories
- New PAIN_POINT_MAP

### Step 3: Update all pages
- Landing page: new value prop, counts, category showcase
- Pricing: update template/category counts
- About: update positioning
- Compare: update if needed
- Demo: update scenes to workflow-based examples
- Any page with "61 templates" or "11 categories"

### Step 4: Verify
- Build passes
- Playwright: every category page loads
- Content accuracy: no old names, correct counts
- Supabase: handle favorites/history for removed templates

## Related Research
- [[Product-Strategy-Pivot]] — Full audit with KEEP/RETHINK/REMOVE classifications
- [[AI-Gap-Analysis]] — Where AI adds real value
- [[Advisor-AI-Usage-Reality]] — What advisors actually use AI for
- [[Advisor-Existing-Systems]] — Systems advisors already have
- [[Template-Competitive-Analysis]] — Competitor template organization
- [[Advisor-Pain-Points]] — Top pain points by frequency
