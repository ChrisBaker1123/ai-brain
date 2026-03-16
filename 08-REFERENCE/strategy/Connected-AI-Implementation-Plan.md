---
type: reference
title: "Connected AI Implementation Plan — Technical Roadmap"
status: active
created: 2026-03-13
updated: 2026-03-16
domain: product
---

# Connected AI Implementation Plan

> Technical roadmap for evolving from copy-paste templates to connected AI workflows.

---

## Phase 1: Copy-Paste Templates (Current — Live)

**Current State** (as of 2026-03-16):
- 68 templates across 8 workflow categories
- Advisor copies template, pastes into Copilot/ChatGPT with client context
- Zero data touches our platform
- Backend: Next.js + Supabase + Claude API (AI Coach only)
- No CRM integrations, no data storage beyond user profiles and template activity

**Advantages**:
- Zero regulatory burden (no data retention, no audit trails)
- Works for 100% of advisors regardless of CRM/system
- Copy-paste model is advisor-friendly (low friction, instant value)
- Wirehouse-compatible (works inside firm security perimeter)

**Limitations**:
- Advisors must manually add context to each template
- No personalization beyond user profile fields
- No CRM integration = missing opportunity for context enrichment

---

## Phase 2: Context-Enriched Templates (Next, ~Q3 2026)

### Goal
Enable advisors to optionally connect CRM, have key contact/context fields auto-populate templates, improve output quality through richer input.

### CRM Integration Architecture

**Target CRMs** (priority order):
1. **Wealthbox** (70+ RIAs actively using, modern REST API, growing market)
2. **Redtail** (8,000+ firms use, legacy but market leader by install base)
3. **Salesforce FSC** (enterprise RIAs, 100+ advisors, complex integrations)

*Future additions*: Schwab InvestmentCenter, Fidelity Wealth Manager, LPL Panoramic

**Connection Model**:
- OAuth 2.0 authorization (advisor authorizes us to access their CRM data)
- Read-only access (we never write to advisor's CRM)
- User-initiated sync (advisor clicks "Connect Wealthbox", not automatic polling)
- Data stored in Supabase, encrypted at rest

**Data Pulled**:
- Client name, contact info (email, phone)
- Meeting history (last meeting date, next meeting scheduled)
- Portfolio summary (AUM, allocation, account types)
- Recent notes (latest CRM entries, truncated to 500 chars)
- Life events (if available in CRM: birthday, anniversary, retirement date)

### Supabase Schema Additions

```sql
-- CRM connections per user
CREATE TABLE crm_connections (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id uuid REFERENCES auth.users(id) ON DELETE CASCADE,
  provider text NOT NULL, -- 'wealthbox', 'redtail', 'salesforce'
  access_token_encrypted text,
  refresh_token_encrypted text,
  scopes text[],
  connected_at timestamptz DEFAULT now(),
  last_sync_at timestamptz,
  status text DEFAULT 'active' -- 'active', 'disconnected', 'error'
);

-- Synced client contacts from CRM
CREATE TABLE synced_contacts (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id uuid REFERENCES auth.users(id) ON DELETE CASCADE,
  crm_connection_id uuid REFERENCES crm_connections(id) ON DELETE CASCADE,
  external_id text NOT NULL, -- CRM's ID for this contact
  display_name text,
  email text,
  phone text,
  last_meeting_date date,
  next_meeting_date date,
  portfolio_summary jsonb, -- {aum, allocation, risk_score}
  notes_summary text, -- Latest CRM notes (truncated)
  synced_at timestamptz DEFAULT now(),
  UNIQUE(crm_connection_id, external_id)
);

-- RLS: users can only see their own connections and contacts
ALTER TABLE crm_connections ENABLE ROW LEVEL SECURITY;
ALTER TABLE synced_contacts ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users see own connections" ON crm_connections
  FOR ALL USING (auth.uid() = user_id);

CREATE POLICY "Users see own contacts" ON synced_contacts
  FOR ALL USING (
    auth.uid() IN (
      SELECT user_id FROM crm_connections WHERE id = synced_contacts.crm_connection_id
    )
  );
```

### Template Auto-Fill Flow

**Step-by-step** (from advisor perspective):
1. Advisor opens a template (e.g., "Meeting Prep Power Brief")
2. If CRM connected: dropdown shows synced contacts (20-50 most recent)
3. Advisor selects contact (e.g., "Sarah Chen")
4. Template auto-fills relevant placeholders:
   - `{{client_name}}` → "Sarah Chen"
   - `{{last_meeting_date}}` → "October 15, 2025"
   - `{{next_meeting_date}}` → "March 20, 2026"
   - `{{aum}}` → "$2.4M"
   - `{{portfolio_allocation}}` → "60% stocks, 40% bonds"
   - `{{recent_notes}}` → "Discussed Roth conversion timing, wants to review tax strategy..."
5. Advisor can edit any auto-filled field before copying
6. Copy to clipboard works exactly as before (template + context go to Copilot)

**Optional**: Add "Re-sync" button to pull latest contact data from CRM (every 24 hours auto-check, or manual)

### Security Requirements

- **Token encryption**: OAuth tokens encrypted at rest using Supabase's built-in encryption
- **Read-only access**: OAuth scopes permit reading contact/account data only, never writing
- **RLS enforced**: Per-user database policies prevent users seeing other users' CRM data
- **Data retention**: Synced contacts deleted after 30 days of user inactivity
- **Audit logging**: Log all CRM API calls (Supabase logs, retained for 90 days)
- **GLBA compliance**: Conduct vendor risk assessment before each CRM integration
- **No PII retention**: Do not store client SSNs, account numbers, or sensitive tax data

### Implementation Steps

1. **Choose first CRM** (Wealthbox)
2. **Read OAuth API docs**, create app in Wealthbox sandbox
3. **Build OAuth flow**: `/api/crm/auth/wealthbox/callback` endpoint
4. **Build sync endpoint**: `/api/crm/sync` (triggered by user action)
5. **Build UI**: "Connect CRM" button in settings, disconnect option
6. **Update template runner**: Add contact dropdown, auto-fill logic
7. **Test with beta advisors** (Mark Halby from DLK, Will Jones from Wells Fargo)
8. **Launch with splash page**: "Try new CRM integration" with FAQ

**Estimated effort**: 4-6 weeks (Wealthbox only), 2-3 weeks per additional CRM

---

## Phase 3: Connected AI Workflows (Future, ~2027+)

### Advanced Capabilities

**Proactive triggers**:
- Before scheduled meeting: Auto-generate meeting prep based on CRM history
- After meeting uploaded: Generate draft follow-up email from transcript
- On life event (birthday, retirement date): Suggest proactive client message

**Multi-channel automation**:
- Draft LinkedIn post suggestions (topic, angle, hashtags)
- Email newsletter content (aggregated from templates)
- Blog post ideas (based on advisor's specialties)

**Integration with connected AI platforms**:
- Accept Hazel data as input (if advisor also uses Hazel)
- Share templates with Hazel users via API
- Bundle positioning: "Templates + Hazel = complete communication + data solution"

### Technical Requirements

- **Webhook integration** with CRM calendars (notify us when meeting scheduled)
- **Transcript processing pipeline** (audio/video → text → structured summary via Claude API)
- **Event-driven template generation** (Supabase Edge Functions or Vercel Cron)
- **Notification system** for advisor review-before-send (in-app, email, Slack)
- **Multi-version history** (track which template version generated which output)

### Partnership Opportunities

**Wealthbox**:
- Modern API, growing RIA market share
- Potential co-marketing: "Wealthbox + Advisor Intelligence = complete advisor platform"
- Revenue share: $X per Advisor Intelligence subscription from Wealthbox referral

**Jump/Zocks**:
- Meeting transcript source for templates
- Complementary positioning: "Jump records meetings, templates create follow-up"
- API integration: Accept Jump transcript → generate follow-up email template

**Altruist/Hazel**:
- Hazel provides data context, we provide communication templates
- Potential bundling: "Buy Hazel, get Advisor Intelligence discount"
- Co-positioning: "Data layer (Hazel) + communication layer (AI Intelligence) = complete advisor AI"

---

## Compliance & Regulatory Considerations

### Copy-Paste Model (Current)
- **Regulatory stance**: Favorable
- **Advisor responsibility**: Clear (advisor reviews before sending)
- **Data retention**: None (no platform data storage beyond user profile)
- **Audit burden**: Minimal (advisor maintains own records)

### CRM-Connected Model (Phase 2)
- **Regulatory stance**: Neutral (depends on implementation)
- **Advisor responsibility**: Still clear, but advisor must ensure CRM data is compliant
- **Data retention**: Synced contacts stored in Supabase (need clear data retention policy)
- **Audit burden**: Moderate (we store contact data, must log access)
- **Required**: SOC 2 Type II certification before enterprise advisor adoption

### Agentic Workflows (Phase 3)
- **Regulatory stance**: Requires careful design
- **Advisor responsibility**: Must remain in the loop (review-before-send, not auto-send)
- **Data retention**: Potentially significant (for audit trail)
- **Audit burden**: High (action trails, version history)
- **Required**: FINRA/SEC guidance review, compliance legal review

### SEC/FINRA Framework

**SEC 2026 Exam Priorities**:
- "Firms must assess regulatory compliance obligations BEFORE deploying GenAI"
- "Review AI output for accuracy before transmitting to clients"
- Emphasis on explainability (advisor can explain AI's reasoning)

**Our Approach**:
- Templates are inherently explainable (template logic is visible to advisor)
- Review-before-send model maintains oversight
- Copy-paste architecture keeps clear audit trail (advisor action initiates everything)

**Messaging to Advisors**:
- "Advisor Intelligence + your CRM = faster communication with full oversight"
- "Every template output can be reviewed, edited, or rejected before sending"
- "No automated sending — you remain in control"

---

## Timeline & Roadmap

| Phase | Timeline | Features | Effort |
|-------|----------|----------|--------|
| **Phase 1** | Live (2026-03-16) | 68 templates, 8 categories, copy-paste | - |
| **Phase 2a** | Q3 2026 | Wealthbox integration, auto-fill | 4-6 weeks |
| **Phase 2b** | Q4 2026 | Redtail + Salesforce integration | 3-4 weeks each |
| **Phase 3a** | Q1 2027 | Proactive meeting prep trigger | 2-3 weeks |
| **Phase 3b** | Q2 2027 | Post-meeting follow-up from transcripts | 3-4 weeks |
| **Phase 3c** | Q3 2027+ | Multi-channel content generation | 4-6 weeks |

---

## Success Metrics

### Phase 2 (CRM Integration)
- **Adoption**: 20%+ of paid advisors connect CRM within 6 months
- **Engagement**: Template copy rate increases 30%+ for users with CRM connected
- **Retention**: CRM-connected users have 15% lower churn
- **NPS**: Advisor feedback confirms auto-fill improves template quality

### Phase 3 (Connected Workflows)
- **Automation rate**: 50%+ of advisor communication uses templates + CRM context
- **Time savings**: Advisors report 5+ hours/week saved vs. manual outreach
- **Client satisfaction**: Clients perceive more personalized communication (NPS data)

---

## Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|-----------|
| CRM API changes break sync | Users lose CRM connection | Version OAuth scopes, test quarterly, maintain API changelog |
| Data breach of synced contacts | Regulatory action, advisor churn | Encryption at rest, RLS per user, SOC 2 Type II, incident response plan |
| Compliance violation (advisor sends non-compliant content) | SEC action against advisor's firm | Maintain clear "advisor responsibility" messaging, document review-before-send |
| Low adoption of CRM integration | Wasted engineering effort | Beta test with 3-5 advisors first, get feedback before major rollout |
| Hazel/connected AI platforms make templates redundant | Product obsolescence | Position as complementary, not competitive; focus on communication, not data |

---

## Related Notes

- [[Connected-AI-Trend]] — Industry analysis and positioning strategy
- [[Competitor-Altruist-Hazel]] — Hazel deep dive
- [[Architecture]] — Current app architecture
- [[Schema]] — Current database schema
- [[Deployment]] — Deployment and env vars
- [[Product-Strategy-Pivot]] — Gap-filler positioning
- [[API-Routes]] — Current API endpoints (reference for new CRM routes)
