---
type: reference
title: "Advisor Intelligence — Business Infrastructure"
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
---

# Business Infrastructure

> Last Updated: 2026-03-24.

## Legal Entity

| Item | Status | Details |
|------|--------|---------|
| **LLC** | Filed March 2026 | Advisor Intelligence LLC, California, single member |
| **EIN** | Pending | IRS call needed (reference 101 due to prior LLC) |
| **State business license** | Needed | Standard California business license |

## Banking & Payments

| Item | Status | Details |
|------|--------|---------|
| **Business bank** | Pending EIN | Mercury (chosen for startup-friendly features) |
| **Payment processing** | Pending EIN | Stripe Invoicing with ACH |
| **Invoicing flow** | Designed | Stripe invoice on 1st of month, auto-recurring after onboarding |

## Insurance

| Type | Status | Provider | Notes |
|------|--------|----------|-------|
| **General Liability** | Purchased | Hiscox | Standard business coverage |
| **Cyber Insurance** | Purchased | Hiscox | Required for handling client tech systems |
| **E&O (Errors & Omissions)** | **NEEDED** | Next Insurance (target) | Critical for consulting. Covers claims of negligent advice or implementation failures. |

## Communications

| Item | Status | Notes |
|------|--------|-------|
| **Domain email** | Needed | cri@advisorintelligence.app (professional requirement) |
| **Phone** | Active | (619) 851-2215 (personal — works for now) |
| **Calendar booking** | Needed | Calendly or Cal.com for team interview scheduling and discovery calls |
| **Password manager** | Needed | 1Password or Bitwarden for client credentials (when we get Salesforce access) |

## Legal Documents

| Document | Status | Notes |
|----------|--------|-------|
| **Engagement letter** | Draft ready | Needs legal review (dad or Dan Skiles) |
| **AI Usage Policy template** | Draft ready | Deliverable for clients |
| **Terms of Service** | On website | advisorintelligence.app/terms |
| **Privacy Policy** | On website | advisorintelligence.app/privacy |
| **NDA** | Needed | For client data access |

## Pending Setup (Priority Order)

1. **EIN** — Blocks banking and payments. Call IRS.
2. **Mercury bank account** — Needs EIN
3. **Stripe** — Needs EIN and bank account
4. **Domain email** — Set up via provider (Google Workspace or similar)
5. **E&O Insurance** — Apply via Next Insurance
6. **Calendar booking** — Set up Calendly/Cal.com, configure on /book page
7. **Password manager** — Set up before receiving client credentials
8. **NEXT_PUBLIC_BOOKING_URL env var** — Critical for website /book page

## Environment Variables Still Needed

| Variable | Purpose | Status |
|----------|---------|--------|
| NEXT_PUBLIC_BOOKING_URL | /book page booking widget | Blocked on Calendly setup |
| STRIPE_WEBHOOK_SECRET | Payment processing | Blocked on Stripe/EIN |
| ADMIN_USER_ID | Admin dashboard access control | Can configure now |
| NEXT_PUBLIC_CRISP_WEBSITE_ID | Live chat widget | Optional |

---

## Related

- [[00-ADVISOR-INTELLIGENCE/INDEX|INDEX]] — Master hub
- [[Business-Model]] — Service definition
- [[Pricing-Framework]] — Pricing details
- [[DLK-HUB]] — First client (needs invoicing setup)
