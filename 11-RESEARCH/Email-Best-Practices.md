---
title: "Email Marketing Best Practices — Advisor SaaS"
type: research
date: 2026-03-13
domain: email
tags: [email, onboarding, marketing, SaaS, research]
---

# Key Takeaways for Advisor Intelligence

1. **Welcome emails get 60-83% open rates** — this is the single highest-impact email you will ever send. Send it immediately (within minutes of signup), keep it plain-text-style with one clear CTA pointing to the dashboard, and set expectations for the trial period.
2. **7-day trials need 6-7 emails** — Day 0 welcome, Day 1 quick win, Day 2 feature highlight, Day 3 social proof / use case, Day 5 value summary + urgency, Day 6 last-day warning, Day 7 expired + path back. Each email should have exactly one CTA.
3. **Behavior-based emails get 3-5x higher engagement** than time-based emails. Track: first template copied, first document opened, AI Coach used, profile completed. Trigger emails based on what users have/haven't done.
4. **Financial services has only 80% inbox placement** (worst of 15 major verticals). Use a subdomain (e.g., `updates.advisorintelligence.app`), implement SPF/DKIM/DMARC, warm the IP gradually, and maintain list hygiene.
5. **Trial-to-paid conversion benchmarks**: 15-25% for opt-in (no card) trials; 7-day trials convert at ~40% for card-required. With guided onboarding, conversions can increase 400-500% vs. passive onboarding. Target: 25%+ for Advisor Intelligence.

---

# Onboarding Email Sequence (7-Day Trial)

## Recommended Timing & Structure

| Email | Timing | Goal | Subject Line Formula |
|-------|--------|------|---------------------|
| 1. Welcome | Immediately (within 5 min) | Set expectations, drive first login | "Welcome to Advisor Intelligence, {{first_name}}" |
| 2. Quick Win | Day 1 (24h after signup) | Get user to copy first template | "Your first AI prompt is ready to copy" |
| 3. Feature Deep Dive | Day 2 | Showcase template categories + Document Builder | "61 templates, 11 categories — find yours" |
| 4. Social Proof / Use Case | Day 3 | Show real advisor workflow example | "How advisors use AI for client emails in 3 minutes" |
| 5. Value Reminder + Urgency | Day 5 | Summarize value, mention trial ending | "You have 2 days left — here's what you've unlocked" |
| 6. Last Day Warning | Day 6 | Create urgency, address objections | "Your trial ends tomorrow — keep your templates?" |
| 7. Trial Expired | Day 7 (or Day 8 morning) | Win-back, offer path to subscribe | "Your Advisor Intelligence trial has ended" |

## Email Content Details

### Email 1: Welcome (Day 0, Immediate)
**Subject**: "Welcome to Advisor Intelligence, {{first_name}}"
**Alternative subjects**: "You're in — here's how to get started" / "Your AI prompt toolkit is ready"
**Goal**: First login + complete profile
**Content**:
- Personal greeting using first name from `full_name.split(" ")[0]`
- One sentence: what Advisor Intelligence does (copy-paste AI prompts for advisors)
- Three quick-start steps: (1) Complete your profile, (2) Browse templates, (3) Copy your first prompt
- Single CTA button: "Open Your Dashboard"
- Brief: "Your 7-day free trial starts now. You have full access to all 61 templates, 20 documents, and AI Coach."
- Sign off from Christopher Baker, Founder
**Design**: Plain-text style, no heavy images. Single-column. Mobile-optimized (14px+ font, 44x44px buttons).

### Email 2: Quick Win (Day 1)
**Subject**: "Your first AI prompt is ready to copy"
**Alternative subjects**: "Try this: a client email in 60 seconds" / "Copy, paste, done — your first template"
**Goal**: Get user to copy their first template
**Content**:
- Show one specific template example (e.g., Client Birthday Email from client_communication)
- Screenshot or text preview of the template
- Explain the copy-paste workflow: Copy prompt > Paste into Copilot > Get polished output
- CTA: "Copy Your First Template"
- Mention: "Your profile data is auto-injected — no setup needed"

### Email 3: Feature Deep Dive (Day 2)
**Subject**: "61 templates, 11 categories — find yours"
**Alternative subjects**: "From prospecting to estate planning — explore your toolkit" / "Did you know about Document Builder?"
**Goal**: Expand awareness of full product
**Content**:
- Highlight 3-4 most popular categories with template counts
- Introduce Document Builder (20 document templates)
- Mention AI Academy tutorials
- CTA: "Browse All Categories"

### Email 4: Social Proof / Use Case (Day 3)
**Subject**: "How advisors use AI for client emails in 3 minutes"
**Alternative subjects**: "See it in action: AI-powered prospect outreach" / "The advisor workflow that saves 5 hours/week"
**Goal**: Show real-world value, build trust
**Content**:
- Walk through a specific use case (e.g., prospecting email for a new retiree lead)
- Show the before (blank page) and after (polished email from Copilot)
- Mention compliance awareness built into every template
- CTA: "Try This Template"
- Note: Do NOT use fake testimonials. Use workflow demonstrations instead.

### Email 5: Value Summary + Urgency (Day 5)
**Subject**: "You have 2 days left — here's what you've unlocked"
**Alternative subjects**: "Your trial recap: templates, documents, and more" / "48 hours left to keep your toolkit"
**Goal**: Summarize value received, create urgency
**Content**:
- If tracking data available: "You've copied X templates and explored Y categories"
- If no tracking: "Here's everything included in your Pro subscription"
- List key features: 61 templates, 20 documents, 18 tutorials, AI Coach, Action Plans
- Price anchor: "$49.99/month — less than one hour of your billable time"
- CTA: "Subscribe Now"

### Email 6: Last Day Warning (Day 6)
**Subject**: "Your trial ends tomorrow — keep your templates?"
**Alternative subjects**: "Last chance: your AI toolkit expires tomorrow" / "Don't lose access to your templates"
**Goal**: Final conversion push, address objections
**Content**:
- Clear statement: trial expires tomorrow
- Address top objection: "Not sure yet? Here's what advisors tell us they use most..."
- Quick FAQ: Can I cancel anytime? (Yes) Is my data safe? (Yes, we never store client data)
- CTA: "Subscribe to Keep Access"
- Softer secondary CTA: "Reply to this email with any questions"

### Email 7: Trial Expired (Day 7/8)
**Subject**: "Your Advisor Intelligence trial has ended"
**Alternative subjects**: "We saved your templates — come back anytime" / "Your toolkit is waiting"
**Goal**: Win-back, leave door open
**Content**:
- Acknowledge the trial has ended
- Remind them their profile and favorites are saved
- Offer: "Subscribe today and pick up right where you left off"
- CTA: "Reactivate Your Account"
- No discount in this first email (save discounts for Day 14+ win-back)
- Sign off: "If the timing isn't right, no worries. We'll be here when you're ready."

## Subject Line Best Practices for Financial Services

- **Length**: 40-60 characters (displays fully on mobile)
- **Personalization**: Use {{first_name}} — 26% higher open rates
- **Questions increase opens by 50%**: "Ready to save 5 hours this week?"
- **Numbers increase opens by 17%**: "3 templates every advisor should try"
- **Avoid spam triggers**: Never use "free," "guaranteed," "act now," "risk-free," "#1," "best"
- **Avoid all-caps** and excessive punctuation
- **Preview text**: Always set — it's the second-most influential factor after subject line

## Benchmarks to Target

| Metric | Industry Average | Target for AI |
|--------|-----------------|---------------|
| Welcome email open rate | 60-83% | 70%+ |
| Onboarding sequence open rate | 40-60% | 45%+ |
| Onboarding click-through rate | 10-20% | 12%+ |
| Trial-to-paid conversion | 15-25% (no card) | 25%+ |
| Overall email open rate (financial services) | 26-39% | 35%+ |
| Click-through rate (financial services) | 3-5% | 4%+ |
| Unsubscribe rate | < 0.5% | < 0.3% |

---

# Nurture Email Sequence (Post-Conversion)

## Cadence
- **Week 1-2**: 2 emails (onboarding continuation)
- **Week 3-4**: 1 email per week (feature highlights)
- **Month 2+**: Biweekly (every 2 weeks)
- **Best send times**: Tuesday-Thursday, 9-11 AM in recipient's timezone

## Email Types

### 1. Feature Highlight Emails (Biweekly)
**Purpose**: Drive deeper product adoption
**Structure**:
- Spotlight one category or feature
- Show a specific template with use case
- Include a "Pro tip" for getting better AI output
- CTA: "Try This Template"

**Example subjects**:
- "New: Estate Planning templates for complex estates"
- "Pro tip: How to get better results from your prospecting prompts"
- "Did you know? Document Builder creates compliance-ready letters"

### 2. New Template Notifications (As Released)
**Purpose**: Show ongoing product development
**Structure**:
- Announce new template(s) added
- Brief description of what problem they solve
- CTA: "View New Templates"

**Example subjects**:
- "3 new templates just added to your toolkit"
- "New: Tax planning prompts for year-end conversations"

### 3. AI Tips & Best Practices (Monthly)
**Purpose**: Help users get more value, reduce churn
**Structure**:
- Teach one technique for better AI outputs
- Show before/after example
- Reference Microsoft Copilot best practices
- CTA: "Read the Full Guide" (link to tutorial)

**Example subjects**:
- "The one word that makes Copilot responses 10x better"
- "Advisor AI tip: How to customize any template for your practice"

### 4. Industry Insights (Monthly)
**Purpose**: Position as thought leader, provide non-product value
**Structure**:
- Brief commentary on AI in financial services
- Regulatory update relevant to AI use
- Link to relevant tutorial or blog post
- CTA: "Read More"

**Example subjects**:
- "What the SEC's latest AI guidance means for your practice"
- "3 ways advisors are using AI this quarter"

## Content That Retains Subscribers
- **Actionable tips** they can implement today
- **Template use cases** with real workflow examples
- **Industry news** relevant to AI adoption
- **Product updates** showing momentum
- **Quick wins** — "Try this in 2 minutes"

## Content to Avoid
- Pure promotional content with no value
- Daily emails (leads to unsubscribes)
- Generic financial advice (they're the advisors)
- Anything that sounds like compliance training

---

# Re-engagement Email Sequence (Churn Prevention)

## Trigger Events & Timing

| Trigger | Email | Timing |
|---------|-------|--------|
| No login for 7 days | Activity Reminder | Day 7 of inactivity |
| No login for 14 days | Value Reminder | Day 14 of inactivity |
| No login for 21 days | Win-back Offer | Day 21 of inactivity |
| No login for 30 days | Final Re-engagement | Day 30 of inactivity |
| Subscription canceled | Cancellation Feedback | Immediately |
| Subscription canceled | Win-back | 14 days post-cancel |
| Subscription canceled | Final Win-back | 30 days post-cancel |

## Email Details

### Email 1: Activity Reminder (7 days inactive)
**Subject**: "We haven't seen you in a while, {{first_name}}"
**Alternative subjects**: "Your templates miss you" / "Quick question about your toolkit"
**Content**:
- Friendly, non-accusatory tone
- Highlight one new template or feature they haven't tried
- Ask if they need help
- CTA: "Log Back In"
- No discount, no pressure

### Email 2: Value Reminder (14 days inactive)
**Subject**: "Here's what you're missing in your toolkit"
**Alternative subjects**: "3 templates other advisors are loving right now" / "Your practice could use this"
**Content**:
- Show 2-3 popular templates from categories they haven't explored
- Mention any new templates added since their last visit
- Include one specific use case with outcome
- CTA: "Explore New Templates"

### Email 3: Win-back Offer (21 days inactive)
**Subject**: "We'd love to have you back — here's 20% off"
**Alternative subjects**: "A special offer to keep your toolkit" / "Can we help? 20% off your next month"
**Content**:
- Acknowledge they've been away
- Offer: 20% off next month (use Stripe promotion code)
- Time-limited: "Valid for 7 days"
- Include a link to book a 15-min walkthrough if they need help
- CTA: "Claim Your Discount"

### Email 4: Final Re-engagement (30 days inactive)
**Subject**: "Is Advisor Intelligence right for you?"
**Alternative subjects**: "One last thing before we stop emailing" / "We'll miss you — but we understand"
**Content**:
- Honest, respectful tone
- Quick survey: Why did you stop using it? (3-4 options)
- Mention the door is always open
- Confirm they'll be moved to low-frequency updates only
- CTA: "Tell Us Why" (survey link)

### Post-Cancellation Win-back (14 days after cancel)
**Subject**: "We've made some updates since you left"
**Content**:
- Highlight 2-3 product improvements or new templates
- No discount yet — lead with value
- CTA: "See What's New"

### Final Win-back (30 days after cancel)
**Subject**: "Come back for 30% off — limited time"
**Content**:
- Stronger offer: 30% off first month back
- Social proof: mention total template count, recent additions
- CTA: "Resubscribe at 30% Off"

## Key Metrics
- **Target reactivation rate**: 15-20% for 7-day inactive
- **Target win-back rate**: 5-10% for canceled users
- **Industry benchmark**: 45% of win-back recipients open subsequent emails
- **Reducing churn by 5% can increase profits by 25-95%**

---

# Newsletter Strategy

## Recommended Approach
- **Frequency**: Biweekly (every 2 weeks)
- **Day/Time**: Tuesday or Wednesday, 9-11 AM ET
- **Format**: Short, scannable sections with links to full content

## Content Mix (Per Newsletter)
1. **One actionable tip** (40%) — "Try this template for X situation"
2. **One product update** (20%) — new template, feature improvement
3. **One industry insight** (20%) — AI in financial services, regulatory update
4. **One resource link** (20%) — tutorial, blog post, or external article

## Newsletter Template Structure
```
Subject: [Tip/Insight] + [Category]
Preview: [Expanded subject with benefit]

Hi {{first_name}},

[1-2 sentence intro tied to current events or season]

--- SECTION 1: TIP OF THE WEEK ---
[Actionable template tip with link]

--- SECTION 2: WHAT'S NEW ---
[Product update or new templates]

--- SECTION 3: INDUSTRY INSIGHT ---
[Brief commentary + link]

--- SECTION 4: RESOURCE ---
[Tutorial or guide link]

---
Christopher Baker
Founder, Advisor Intelligence
[Unsubscribe] | [Manage Preferences]
[Physical Address]
```

## What Gets Shared in Advisor Circles
- Practical workflow tips they can implement immediately
- AI prompt techniques that produce better outputs
- Regulatory updates about AI use in financial services
- Tools and integrations that save time
- Comparison content (e.g., Copilot vs. ChatGPT for advisors)

## What Does NOT Get Shared
- Pure product promotion
- Generic AI news without advisor context
- Overly long essays
- Content without clear takeaways

---

# Technical Implementation with Resend

## Architecture Overview
```
app/src/
├── lib/
│   └── email/
│       ├── resend.ts          # Resend client initialization
│       ├── templates/         # React Email templates
│       │   ├── welcome.tsx
│       │   ├── quick-win.tsx
│       │   ├── feature-deep-dive.tsx
│       │   ├── use-case.tsx
│       │   ├── value-summary.tsx
│       │   ├── last-day.tsx
│       │   ├── trial-expired.tsx
│       │   ├── activity-reminder.tsx
│       │   ├── win-back.tsx
│       │   └── newsletter.tsx
│       └── sequences/
│           ├── onboarding.ts  # 7-day trial sequence logic
│           ├── nurture.ts     # Post-conversion nurture
│           └── re-engagement.ts # Churn prevention
├── app/
│   └── api/
│       └── email/
│           ├── send/route.ts      # Send individual emails
│           ├── webhook/route.ts   # Resend webhooks (open/click tracking)
│           └── cron/route.ts      # Vercel cron for scheduled sends
```

## Resend Setup

### 1. Dependencies
```bash
npm install resend @react-email/components react-email
```

### 2. Environment Variables
```env
RESEND_API_KEY=re_xxxxxxxxxxxx
RESEND_FROM_EMAIL=Christopher Baker <hello@advisorintelligence.app>
RESEND_REPLY_TO=chris@advisorintelligence.app
```

### 3. Domain Configuration
- Use subdomain: `updates.advisorintelligence.app` (isolates email reputation)
- Add DNS records in domain registrar: MX, SPF, DKIM, DMARC
- Verify domain in Resend dashboard before sending
- Use "Sending Access" API key permission in production (principle of least privilege)

### 4. Sending Strategy
| Email Type | Resend Feature | Notes |
|-----------|---------------|-------|
| Transactional (welcome, password reset) | Send Email API | Single recipient, triggered by user action |
| Trial sequence (day 1-7) | Send Email API | Triggered by cron checking trial day |
| Batch notifications | Batch Send API | Up to 100 emails per call |
| Newsletter/broadcast | Broadcast API | Marketing emails, requires unsubscribe |

### 5. Email Template Design
- Use `@react-email/components` for responsive templates
- Single-column layout for mobile optimization
- 80:20 text-to-image ratio
- Minimum 14px font for mobile readability
- Button CTAs: minimum 44x44px touch target
- Include plain-text fallback for every HTML email
- Always include: unsubscribe link, physical address, reply-to address

### 6. Deliverability Best Practices
- **Authentication**: SPF + DKIM + DMARC on sending domain
- **Warm-up**: Start with low volume (50-100/day), increase by 20% per week
- **List hygiene**: Remove hard bounces immediately, remove soft bounces after 3 attempts
- **Engagement monitoring**: Track opens/clicks via Resend webhooks
- **Spam score testing**: Test every template before sending to full list
- **Send time**: Avoid top-of-hour sends (10:07 AM > 10:00 AM)
- **Financial services note**: Expect ~80% inbox placement (industry worst). Compensate with strong authentication, clean lists, and high-value content.

### 7. Webhook Events to Track
```typescript
// Resend webhook events
type ResendEvent =
  | 'email.sent'
  | 'email.delivered'
  | 'email.delivery_delayed'
  | 'email.complained'
  | 'email.bounced'
  | 'email.opened'
  | 'email.clicked';
```

### 8. Database Schema for Email Tracking
```sql
-- Track email sends and engagement
CREATE TABLE email_events (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES auth.users(id),
  email_type TEXT NOT NULL, -- 'welcome', 'day1', 'day2', etc.
  sequence TEXT NOT NULL, -- 'onboarding', 'nurture', 're-engagement'
  sent_at TIMESTAMPTZ DEFAULT now(),
  opened_at TIMESTAMPTZ,
  clicked_at TIMESTAMPTZ,
  bounced BOOLEAN DEFAULT false,
  resend_id TEXT -- Resend message ID for tracking
);

-- Track which sequence step each user is on
CREATE TABLE email_sequence_state (
  user_id UUID PRIMARY KEY REFERENCES auth.users(id),
  current_sequence TEXT, -- 'onboarding', 'nurture', 're-engagement'
  current_step INT DEFAULT 0,
  last_email_sent_at TIMESTAMPTZ,
  trial_start_date TIMESTAMPTZ,
  last_login_at TIMESTAMPTZ,
  subscribed BOOLEAN DEFAULT true
);
```

### 9. Vercel Cron Configuration
```json
// vercel.json
{
  "crons": [
    {
      "path": "/api/email/cron",
      "schedule": "0 14 * * *"  // 9 AM ET (14:00 UTC) daily
    }
  ]
}
```

The cron job checks each user's sequence state and sends the appropriate email based on their trial day, subscription status, and last activity.

---

# Related Notes

- [[Email-Strategy]]
- [[Marketing-Strategy]]
- [[Brand-Voice]]
- [[Content-Calendar]]
- [[Email-Compliance-Guide]]
- [[Competitor-Email-Teardown]]

---

# Sources

- [ProductLed: SaaS Onboarding Email Best Practices](https://productled.com/blog/user-onboarding-email-best-practices)
- [Knock: 16 Welcome Email Examples](https://knock.app/blog/welcome-email-examples)
- [SaaS Academy: Free Trial Email Sequences](https://www.saasacademy.com/blog/free-trial-emails)
- [Mailmodo: SaaS Churn Prevention Sequence](https://www.mailmodo.com/email-flow/saas-email-flow/saas-churn-prevention-email-sequence/)
- [Validity: Financial Services Email Challenge](https://www.validity.com/blog/tougher-than-the-rest-the-financial-services-email-challenge/)
- [Resend: Sending Features Guide](https://resend.com/docs/knowledge-base/what-sending-feature-to-use)
- [SaaS Hero: B2B SaaS Conversion Benchmarks 2026](https://www.saashero.net/customer-retention/b2b-saas-conversion-benchmarks-journey/)
- [Sequenzy: Trial Expiration Emails](https://www.sequenzy.com/blog/how-to-set-up-trial-expiration-emails)
- [Bedrock: Email Open Rate Strategies for Financial Professionals](https://bedrockfs.com/email-open-rate-strategies-best-practices-for-independent-financial-professionals/)
- [HubSpot: Email Marketing Benchmarks](https://blog.hubspot.com/sales/average-email-open-rate-benchmark)
