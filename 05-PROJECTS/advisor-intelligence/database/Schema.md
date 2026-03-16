# Database Schema

#database #supabase #schema

**Database**: Supabase PostgreSQL 17.6.1.063
**Project ID**: jrhbeoffypjnqtrcmzsy
**Region**: us-west-2
**Status**: ACTIVE_HEALTHY
**Created**: 2026-03-10

## Tables (9 in public schema)

### 1. advisor_profiles (4 rows) — Core user data
| Column | Type | Nullable | Default | Notes |
|--------|------|----------|---------|-------|
| `id` | uuid | NO | `gen_random_uuid()` | PK |
| `user_id` | uuid | YES | - | FK to auth.users, UNIQUE |
| `full_name` | text | YES | - | Use `.split(" ")[0]` for first name |
| `firm_name` | text | YES | - | |
| `firm_type` | text | YES | - | ria, wirehouse, ibd, hybrid |
| `aum_range` | text | YES | - | |
| `team_size` | integer | YES | - | |
| `years_experience` | integer | YES | - | |
| `primary_crm` | text | YES | - | |
| `planning_software` | text | YES | - | |
| `pain_points` | text[] | YES | - | Array, used for dashboard personalization |
| `ai_confidence` | text | YES | - | |
| `compliance_framework` | text | YES | - | |
| `credentials` | text[] | YES | - | CFP®, CFA®, etc. |
| `client_specialties` | text[] | YES | - | |
| `tone_preference` | text | YES | `'professional_warm'` | formal, professional_warm, conversational |
| `client_households` | text | YES | - | |
| `compliance_acknowledged` | boolean | YES | `false` | |
| `compliance_acknowledged_at` | timestamptz | YES | - | |
| `tos_accepted` | boolean | YES | `false` | |
| `tos_accepted_at` | timestamptz | YES | - | |
| `requires_firm_approval` | boolean | YES | `false` | |
| `firm_approval_status` | text | YES | - | |
| `crd_number` | text | YES | - | SEC/FINRA registration |
| `sec_registration_status` | text | YES | - | |
| `sec_aum` | bigint | YES | - | |
| `sec_num_accounts` | integer | YES | - | |
| `sec_filing_date` | date | YES | - | |
| `finra_licenses` | text[] | YES | - | |
| `finra_disclosures` | integer | YES | `0` | |
| `edgar_services_summary` | text | YES | - | |
| `edgar_fee_structure` | text | YES | - | |
| `profile_hash` | text | YES | - | For cache invalidation |
| `subscription_tier` | text | YES | `'free'` | free or pro |
| `stripe_customer_id` | text | YES | - | Stripe integration |
| `stripe_subscription_id` | text | YES | - | Stripe integration |
| `created_at` | timestamptz | YES | `now()` | |
| `updated_at` | timestamptz | YES | `now()` | Auto-updated by trigger |

### 2. chat_conversations (1 row) — AI Coach conversation threads
| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| `id` | uuid | NO | `gen_random_uuid()` |
| `user_id` | uuid | NO | - |
| `title` | text | NO | `'New conversation'` |
| `preview` | text | NO | `''` |
| `messages` | jsonb | NO | `'[]'::jsonb` |
| `message_count` | integer | NO | `0` |
| `created_at` | timestamptz | YES | `now()` |
| `updated_at` | timestamptz | YES | `now()` |

### 3. chat_messages (16 rows) — Individual chat messages
| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| `id` | uuid | NO | `gen_random_uuid()` |
| `user_id` | uuid | YES | - |
| `role` | text | NO | - | "user" or "assistant" |
| `content` | text | NO | - |
| `tokens_used` | integer | YES | - |
| `created_at` | timestamptz | YES | `now()` |

### 4. generation_outputs (8 rows) — Template copy history + favorites
| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| `id` | uuid | NO | `gen_random_uuid()` |
| `user_id` | uuid | YES | - |
| `prompt_id` | text | NO | - |
| `prompt_title` | text | NO | - |
| `category` | text | NO | - |
| `user_inputs` | jsonb | NO | `'{}'::jsonb` |
| `generated_content` | text | NO | - |
| `model` | text | NO | - |
| `is_favorited` | boolean | YES | `false` |
| `created_at` | timestamptz | YES | `now()` |

### 5. generation_logs (0 rows) — API usage tracking
| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| `id` | uuid | NO | `gen_random_uuid()` |
| `user_id` | uuid | YES | - |
| `toolkit_id` | uuid | YES | - | FK → toolkits.id |
| `model` | text | NO | - |
| `input_tokens` | integer | YES | - |
| `output_tokens` | integer | YES | - |
| `cost_cents` | integer | YES | - |
| `profile_hash` | text | YES | - |
| `template_version` | text | YES | - |
| `duration_ms` | integer | YES | - |
| `created_at` | timestamptz | YES | `now()` |

### 6. prompt_feedback (0 rows) — Template ratings
| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| `id` | uuid | NO | `gen_random_uuid()` |
| `prompt_id` | uuid | YES | - | FK → prompts.id |
| `user_id` | uuid | YES | - |
| `rating` | integer | YES | - |
| `feedback_text` | text | YES | - |
| `created_at` | timestamptz | YES | `now()` |

### 7. prompts (0 rows) — Server-side prompts (legacy, unused)
### 8. template_versions (0 rows) — Version tracking (legacy, unused)
### 9. toolkits (0 rows) — Toolkit instances (legacy, unused)

**Note**: Tables 7-9 (`prompts`, `template_versions`, `toolkits`) are from an earlier architecture where prompts were generated server-side. The app now uses client-side copy-paste from `lib/prompts-data.json`. These tables have 0 rows and are not actively used.

## Actively Used Tables
1. **advisor_profiles** — User profiles and subscriptions
2. **chat_conversations** — AI Coach conversation threads
3. **chat_messages** — AI Coach message history
4. **generation_outputs** — Template usage history and favorites

## Indexes (15 total)
| Table | Index | Type |
|-------|-------|------|
| advisor_profiles | `advisor_profiles_pkey` | UNIQUE btree (id) |
| advisor_profiles | `advisor_profiles_user_id_key` | UNIQUE btree (user_id) |
| chat_conversations | `chat_conversations_pkey` | UNIQUE btree (id) |
| chat_conversations | `idx_chat_conversations_updated` | btree (user_id, updated_at DESC) |
| chat_conversations | `idx_chat_conversations_user_id` | btree (user_id) |
| chat_messages | `chat_messages_pkey` | UNIQUE btree (id) |
| generation_outputs | `generation_outputs_pkey` | UNIQUE btree (id) |
| generation_outputs | `idx_generation_outputs_user_created` | btree (user_id, created_at DESC) |
| generation_outputs | `idx_generation_outputs_user_favorited` | PARTIAL btree (user_id, is_favorited) WHERE is_favorited = true |

## Extensions
- `plpgsql` 1.0 — Procedural SQL
- `pgcrypto` 1.3 — Cryptographic functions
- `pg_stat_statements` 1.11 — Query statistics
- `supabase_vault` 0.3.1 — Secret storage
- `uuid-ossp` 1.1 — UUID generation
- `pg_graphql` 1.5.11 — GraphQL API

## Entity Relationships
```
auth.users (1) ──── (1) advisor_profiles (via user_id)
advisor_profiles (1) ──── (N) chat_conversations (via user_id)
advisor_profiles (1) ──── (N) chat_messages (via user_id)
advisor_profiles (1) ──── (N) generation_outputs (via user_id)
toolkits (1) ──── (N) prompts (via toolkit_id) [LEGACY]
toolkits (1) ──── (N) generation_logs (via toolkit_id) [LEGACY]
prompts (1) ──── (N) prompt_feedback (via prompt_id) [LEGACY]
```

## Related Notes
- [[RLS-Policies]] — Row-level security for all tables
- [[Auth-Flow]] — How users are created
- [[User-Model]] — Profile data model
- [[API-Routes]] — Routes that query these tables
- [[Architecture]] — How data flows through the app
