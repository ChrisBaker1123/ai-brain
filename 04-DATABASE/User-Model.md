# User Model

#database #auth #user

## Profile Fields (advisor_profiles)

### Collected During Onboarding
| Field | Type | Screen | Required |
|-------|------|--------|----------|
| `full_name` | text | Screen 1 | Yes |
| `firm_type` | text | Screen 1 | Yes (ria, wirehouse, ibd, hybrid) |
| `aum_range` | text | Screen 1 | Yes |
| `client_specialties` | text[] | Screen 1 | No |
| `pain_points` | text[] | Screen 1 | No |
| `tone_preference` | text | Screen 2 | Yes (formal, professional_warm, conversational) |

### Auto-Set by System
| Field | When | Value |
|-------|------|-------|
| `user_id` | Signup trigger | auth.users.id |
| `subscription_tier` | Default | 'free' |
| `compliance_acknowledged` | Default | false |
| `tos_accepted` | Default | false |
| `created_at` | Insert | now() |
| `updated_at` | Every update | now() (via trigger) |

### Set by Stripe Integration
| Field | When |
|-------|------|
| `stripe_customer_id` | Stripe checkout completed |
| `stripe_subscription_id` | Subscription created |
| `subscription_tier` | Updated to 'pro' on subscription |

### SEC/FINRA Fields (Not Collected in UI)
Fields exist for potential future integration with regulatory databases:
`crd_number`, `sec_registration_status`, `sec_aum`, `sec_num_accounts`, `sec_filing_date`, `finra_licenses`, `finra_disclosures`, `edgar_services_summary`, `edgar_fee_structure`

## How Profile Data Is Used

### Template Personalization (prompt-runner.tsx)
`buildAdvisorContext()` injects profile data into templates:
- `{{advisor_name}}` → full_name
- `{{firm_name}}` → firm_name
- `{{firm_type}}` → firm_type (formatted label)
- `{{credentials}}` → credentials array (formatted)
- Remaining `{{placeholders}}` → `[UPPERCASE INSTRUCTIONS]`

### AI Coach Context (system-prompt.ts)
`buildSystemPrompt()` creates XML-tagged advisor context:
- First name, firm name, firm type
- AUM range, specialties
- Pain points, tone preference
- Credentials (properly formatted: CFP®, CFA®, etc.)
- Firm-type-specific compliance rules

### Dashboard Personalization
- Welcome message uses `full_name.split(" ")[0]` for first name
- Action cards filtered by `pain_points` array
- Compliance references adapted by `firm_type`

### Admin Analytics
Admin dashboard reads all profiles (via admin client bypassing RLS):
- User counts by `subscription_tier`
- Breakdown by `firm_type`
- AUM distribution

## Important Bugs Fixed
- `first_name` column doesn't exist — always use `full_name` + `.split(" ")[0]`
- Settings page was saving firstName back, destroying last names — fixed to save fullName
- Multi-select fields use pipe `|` delimiter (not comma) to avoid collisions with values containing commas

## Related Notes
- [[Schema]] — Full table schema
- [[Auth-Flow]] — How profiles are created
- [[Component-Prompt-Runner]] — How profile data injects into templates
- [[Page-Profile]] — Onboarding UI
- [[Page-Settings]] — Profile editing
- [[Page-Dashboard]] — Personalized dashboard
