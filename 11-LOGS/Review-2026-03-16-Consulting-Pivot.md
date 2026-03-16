---
type: log
title: "Business Review — Consulting Pivot (2026-03-16)"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: business
---

# Business Review — Consulting Pivot (2026-03-16)

---

## 1. Implementation Score: 7/10

**What was done well:**
- Research was thorough: 8 parallel agents, real data, honest wirehouse assessment
- Business model is well-designed: 3 tiers match market benchmarks (Carson at $995)
- Homepage nails the consulting positioning: Cri is the product, IT analogy works, advisor-friendly language throughout
- Pricing page is clean and consulting-focused
- About page builds genuine trust through honest storytelling
- Book page is discovery-call focused with phone fallback
- CLAUDE.md and vault updated to reflect the pivot

**What was missed (3 points deducted):**
- 5+ marketing pages still had old toolkit-first copy at deploy time (compare, roadmap, preview, trust, terms). Some fixed in this review, some still pending.
- No booking widget — the /book page falls back to an email link, which is a friction point
- Homepage nav has no mobile hamburger menu — navigation broken on small screens
- Old pricing ($50/month, "free during early access") persisted in compare page, terms, OG image, and settings until caught in this review
- The roadmap page is entirely SaaS-focused and contradicts the consulting pivot
- No /how-it-works standalone page exists (only a homepage section)

---

## 2. Issues Found and Fixed

| Issue | Severity | Status |
|-------|----------|--------|
| Compare page: "$50/month flat" pricing | CRITICAL | Fixed |
| Compare page: "Free (early access)" CTA | CRITICAL | Fixed |
| Pricing layout metadata: "Free During Early Access" | CRITICAL | Fixed |
| OG image: "Free during early access" | HIGH | Fixed |
| Homepage nav: blue div instead of logo | HIGH | Fixed |
| Trust page: "Get Started" CTA → signup | MEDIUM | Fixed |
| Roadmap page: SaaS-focused copy | HIGH | NOT FIXED (needs full rewrite) |
| Preview page: toolkit-first positioning | HIGH | NOT FIXED (needs rewrite) |
| Terms page: "$50/month" references | MEDIUM | NOT FIXED (lower priority) |
| Settings: "Early Access - Free" | LOW | NOT FIXED (internal only) |
| Homepage: no mobile hamburger menu | HIGH | NOT FIXED (needs client component) |
| Demo page: SaaS demo positioning | MEDIUM | NOT FIXED |

---

## 3. "Miss Us" Assessment: PASSES — with caveats

**Does this business pass the Dan Skiles test?** Yes, if executed correctly.

The model has 10 engineered retention hooks documented in [[Retention-Strategy]]:
1. Accumulated practice knowledge (switching cost)
2. Living roadmap (evolving dependency)
3. Monthly AI impact brief (ROI reset)
4. Quick-call trusted advisor status (behavioral habit)
5. Proactive industry intelligence (information dependency)
6. Workflow embedding (operational integration)
7. Quarterly business reviews (value ceremonies)
8. Progressive template customization (compounding personalization)
9. Client peer network (future, 5+ clients)
10. Scope expansion (surface area growth)

**The caveat**: These hooks only work if Cri ACTUALLY DELIVERS them consistently. A monthly brief that arrives late or a QBR that gets skipped destroys the habit. The playbook must be followed religiously for the first 6 months.

**Biggest retention risk**: Months 4-5. After the audit high wears off and before the deep relationship forms. This is where the monthly brief, proactive intelligence, and quick-call habit must carry the value perception.

---

## 4. Retention Risk

**Biggest risk**: The "I got what I needed" cancellation at month 3-4.

**Mitigation**: The monthly AI brief, living roadmap updates, and progressive template customization create ongoing value that can't be replicated with a one-time engagement. The honest answer to "should I cancel?" is: "The AI landscape changes monthly. I keep you current. If you're confident you can stay current on your own, cancel. Most advisors find they can't."

**Second biggest risk**: Cri's capacity as a full-time student. At 10+ clients with monthly calls, QBRs, briefs, and on-demand support, time management becomes critical.

---

## 5. 12-Month Viability: STRONG

The consulting model is viable because:
- The AI landscape changes monthly (structural demand)
- Accumulated practice knowledge creates switching costs
- $997/month is validated by Carson Coaching's identical pricing
- Independent RIAs (~3,200 target firms) actively need this
- No direct competitor occupies the "bilingual AI consultant for advisors" position
- The model feeds the 3-phase career plan (consulting → installations → advising)

See [[Future-Outlook]] for 12/24/36 month assessment.

---

## 6. DLK Readiness: 8/10

**Ready:**
- Proposal written ([[dlk-proposal.md]])
- Business model documented and priced
- Website reflects consulting positioning
- Contact notes are thorough (Mark, Don, full team documented)
- The SDSU/Fowler connection is genuine and well-documented

**Not ready:**
- No booking widget on /book page (falls back to email)
- Roadmap page still shows SaaS positioning (if Don clicks through)
- No way to show a "consulting in action" example (no case studies yet — expected for first client)

**Recommendation**: Before the DLK follow-up, get a Calendly link set up so the /book page works properly. The email fallback is fine for a first client but doesn't look polished.

---

## 7. Remaining Gaps (Next Session)

**Priority 1 (before DLK pitch):**
- [ ] Set up Calendly/Cal.com and add NEXT_PUBLIC_BOOKING_URL env var
- [ ] Add mobile hamburger menu to homepage nav (it's broken on mobile)

**Priority 2 (before going to market broadly):**
- [ ] Rewrite /roadmap page for consulting positioning
- [ ] Rewrite or remove /preview page (or reposition as "AI Toolkit" resource page)
- [ ] Update /terms with consulting language
- [ ] Remove /demo page or redirect to /book

**Priority 3 (ongoing):**
- [ ] Build first monthly AI brief template
- [ ] Create AI audit questionnaire template
- [ ] Design the Practice Intelligence File format
- [ ] Set up Stripe for consulting tier billing
- [ ] Update LinkedIn profile and content to reflect consulting positioning

---

## 8. Top 3 Things Cri Should Do This Week

1. **Set up Calendly and connect to /book page.** This is the #1 conversion path. Every CTA points here. An email fallback loses prospects. Takes 30 minutes. Do it today.

2. **Send the DLK proposal to Mark Halby.** Don Dempster is back from Europe. The proposal is ready. Don't wait for the website to be perfect — the proposal is the pitch, not the website. Call Mark, send the PDF, schedule the follow-up.

3. **Post on LinkedIn about the pivot.** Not "I pivoted my business." Instead: "I've been working with financial advisors on AI for the past year. Here's what I learned: advisors don't need more tools. They need someone who speaks both AI and finance. That's what I do now." One post. Authentic. No sales pitch. Let people ask questions in the comments.

---

## Related Notes

- [[Business-Model]] — Full model
- [[Consulting-Playbook]] — Engagement structure
- [[Retention-Strategy]] — "Miss us" engineering
- [[Client-Experience-Map]] — Month-by-month client journey
- [[Future-Outlook]] — 12/24/36 month assessment
- [[DLK-Engagement]] — First client opportunity
- [[Decision-2026-03-16-Pivot-To-Consulting]] — The decision record
