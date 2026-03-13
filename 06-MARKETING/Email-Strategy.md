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

## Related Notes
- [[Marketing-Strategy]] — Email in overall strategy
- [[Brand-Voice]] — Email tone
- [[Auth-Flow]] — Signup triggers
- [[Deployment]] — Resend env var needed
- [[Backlog]] — Email setup is pending
