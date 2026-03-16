# Page: Book a Demo

#page #marketing

## Route
`/book` — Public

## Layout
Two-column: Left (info + bullets), Right (CTA card)

## Current State
- Falls back to **mailto link** (support@advisorintelligence.com) because `NEXT_PUBLIC_BOOKING_URL` env var is not set
- Should use Cal.com or Calendly embed when configured
- Pre-filled email subject: "Demo Request - Advisor Intelligence"
- "We'll respond within 2 hours during business days"
- Four bullets: 15-min call, screen share, help setup, personalized walkthrough

## Improvement Needed
- Set up Cal.com or Calendly account
- Set `NEXT_PUBLIC_BOOKING_URL` env var in Vercel
- Embedded calendar is much higher conversion than mailto

## SEO
- **Title**: "Book a Demo | Advisor Intelligence"

## Related Notes
- [[Deployment]] — Env var configuration
- [[Backlog]] — Booking setup is pending
