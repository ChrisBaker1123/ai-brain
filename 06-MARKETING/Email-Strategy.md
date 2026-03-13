# Email Strategy

#marketing #email

## Infrastructure
- **Provider**: Resend (planned, not yet configured)
- **Status**: `RESEND_API_KEY` env var is empty — email not functional yet

## Onboarding Sequence (5 emails)

### Email 1: Welcome (Immediate)
- **Subject**: "Your toolkit is ready — here's where to start"
- **Purpose**: Activation — get them to copy their first template
- **Content**: Welcome, link to dashboard, suggest starting with "Meeting Prep Power Brief"
- **CTA**: "Copy your first template"

### Email 2: Quick Win (Day 2)
- **Subject**: "Save 2 hours this week with one template"
- **Purpose**: Show immediate value
- **Content**: Highlight the Client Email template, show before/after time comparison
- **CTA**: "Try this template"

### Email 3: Deep Dive (Day 4)
- **Subject**: "The AI feature most advisors miss"
- **Purpose**: Introduce Document Builder or Action Plans
- **Content**: Walk through a specific document template or action plan scenario
- **CTA**: "Explore Document Builder"

### Email 4: Compliance Trust (Day 7)
- **Subject**: "How to use AI without worrying about compliance"
- **Purpose**: Address the #1 objection
- **Content**: Explain copy-paste model, compliance references, firm-type awareness
- **CTA**: "See Trust Center"

### Email 5: Check-in (Day 14)
- **Subject**: "How's your toolkit working?"
- **Purpose**: Gather feedback, re-engage inactive users
- **Content**: Ask what they've used, what they need, offer a demo call
- **CTA**: "Reply to this email" or "Book a call"

## Nurture Sequence (Monthly)
- New template announcements
- AI tips for advisors
- Feature updates
- Industry news commentary

## Re-engagement (After 30 days inactive)
- "We've added X new templates since you last visited"
- "Advisors are saving Y hours/week — are you?"

## Trigger Points
| Trigger | Email |
|---------|-------|
| Signup | Welcome (Email 1) |
| Day 2 no activity | Quick Win (Email 2) |
| Day 4 | Deep Dive (Email 3) |
| Day 7 | Compliance Trust (Email 4) |
| Day 14 | Check-in (Email 5) |
| 30 days inactive | Re-engagement |
| New feature launch | Announcement |

## Research-Informed Updates (2026-03-13)

Based on comprehensive research across SaaS onboarding benchmarks, competitor teardowns (Altruist, Wealthbox, Orion, Notion, Linear, Figma), SEC/FINRA compliance, and email conversion data. Full research in `11-RESEARCH/Email-Best-Practices.md`, `Email-Compliance-Guide.md`, and `Competitor-Email-Teardown.md`.

### Critical Change #1: Expand from 5 emails to 7 (match the 7-day trial)

Research consensus: 4-6 emails during trial is optimal, but our 7-day trial with $49.99/mo paywall needs daily touchpoints. Add Day 1 (Quick Win) and Day 6 (Trial Ending Tomorrow) emails. Current sequence has a 12-day gap between Email 4 (Day 7) and Email 5 (Day 14) — this is a conversion dead zone during the most critical period.

**Revised sequence:**
- Day 0: Welcome + Instant Value (keep, but improve — see below)
- Day 1: Quick Win — "Try this with Copilot — takes 90 seconds" → guide to copy first template (THE AHA MOMENT)
- Day 2: Feature Discovery — "Beyond templates: the Document Builder" → introduce Document Builder
- Day 3: Compliance Trust (keep Email 4 content, move earlier)
- Day 5: Usage Nudge — "[FirstName], you've used [X] templates so far" → personalized stats
- Day 6: Trial Ending — "Your trial ends tomorrow, [FirstName]" → feature loss + value recap
- Day 7: Convert or Conversation — "Your trial just ended" → subscribe CTA + extension offer

### Critical Change #2: Behavioral triggers, not just time-based

Research finding: Behavioral triggers get 3-5x higher engagement than calendar-based sends (ProductLed, Encharge data). Add these triggers:

| Trigger | Email | Subject | CTA |
|---------|-------|---------|-----|
| Signup, no login within 4 hrs | Nudge | "Your toolkit is waiting, [FirstName]" | "Log in to your dashboard" → `/dashboard` |
| First template copied | Celebrate + next step | "Nice work! Here's your next move" | "Try the Document Builder" → `/documents` |
| No login for 3 days (during trial) | Re-engage | "[FirstName], your trial is slipping away" | "Pick up where you left off" → `/dashboard` |
| Visited pricing page, didn't convert | Objection handling | "$49.99 vs. the cost of your time" | "Start your subscription" → `/subscribe` |
| High usage + Day 5 | Early convert | "Love it? Lock in your access" | "Subscribe now" → `/subscribe` |

### Critical Change #3: Personalize Email 1 by firm type and pain points

Research insight: Notion personalizes onboarding by account type from Email 1 (personal vs. team), seeing 27% higher activation. We should do the same using onboarding profile data.

**Replace current Email 1 with personalized variants:**
- RIA + client_communication pain point → Subject: "Your client communication templates are ready, [FirstName]" → CTA links to `/toolkit/client-communication`
- Independent + prospecting pain point → Subject: "[FirstName], your prospecting toolkit is set up" → CTA links to `/toolkit/prospecting`
- Default (no profile data) → Subject: "Your first template is ready, [FirstName]" → CTA links to top category

### Critical Change #4: Add re-engagement and win-back sequences

Current strategy has a single re-engagement line. Research shows win-back emails recover 5-15% of churned users. Add:

**Inactive trial (3+ days no activity):**
- Email 1 (Day 3 inactive): Subject: "[FirstName], we saved your spot" → link to fastest-value template
- Email 2 (Day 5 inactive): Subject: "What's holding you back?" → reply-to from founder

**Churned subscribers (4-email sequence over 90 days):**
- Day 3: Subject: "We'll keep the light on, [FirstName]" → account saved, reactivate link
- Day 30: Subject: "[X] new templates since you left" → feature updates
- Day 60: Subject: "A better deal for you, [FirstName]" → 20% off for 3 months
- Day 90: Subject: "Last check-in from Advisor Intelligence" → feedback survey, final email

### Critical Change #5: Compliance footer on every email

CAN-SPAM penalties are $51,744 per violation. Every email must include:
```
Advisor Intelligence | AI-Powered Prompt Toolkit for Financial Advisors
[Physical Address]
This is a commercial message. You received this because you signed up at advisorintelligence.app.
Our templates include compliance references but do not constitute legal or regulatory advice.
[Unsubscribe] | [Email Preferences] | [Privacy Policy]
(c) 2026 Advisor Intelligence.
```

### Critical Change #6: Subject line optimization

Research data: Questions boost opens 50%, numbers boost 17%. Keep under 45 characters for mobile. Avoid spam triggers ("free," "guaranteed," "act now") — especially flagged in financial services.

**Revised subject lines for existing sequence:**
| Email | Old Subject | New Subject | Why |
|-------|-------------|-------------|-----|
| Welcome | "Your toolkit is ready — here's where to start" | "Your first template is ready, [FirstName]" | Personalization + specific + shorter |
| Quick Win | "Save 2 hours this week with one template" | "Try this with Copilot — takes 90 seconds" | Specific tool + time = curiosity |
| Deep Dive | "The AI feature most advisors miss" | "Beyond templates: the Document Builder" | Concrete feature name beats vague curiosity |
| Compliance | "How to use AI without worrying about compliance" | "'Is this compliant?' — here's the answer" | Question format (50% open boost) |
| Check-in | "How's your toolkit working?" | "You've used [X] templates so far" | Personalized data beats generic question |

### Benchmark Targets
- Welcome email open rate: 40%+ (industry: 40-60% for welcome emails)
- Sequence average open rate: 30%+ (financial services average: 25-28%)
- Click-through rate: 8%+ (financial services average: 4.88%)
- Trial-to-paid conversion: 25%+ (B2B median: 18.5%, top quartile: 35-45%)

### Sender Identity
Per Altruist's approach: use `christopher@advisorintelligence.app` (founder name) not `noreply@`. Personal sender names increase open rates in financial services.

## Related Notes
- [[Marketing-Strategy]] — Email in overall strategy
- [[Brand-Voice]] — Email tone
- [[Auth-Flow]] — Signup triggers
- [[Deployment]] — Resend env var needed
- [[Backlog]] — Email setup is pending
- [[Email-Best-Practices]] — Full research (11-RESEARCH)
- [[Email-Compliance-Guide]] — SEC/FINRA/CAN-SPAM rules (11-RESEARCH)
- [[Competitor-Email-Teardown]] — Altruist, Wealthbox, Orion, Notion, Figma analysis (11-RESEARCH)
