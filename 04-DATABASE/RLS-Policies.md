# RLS Policies

#database #security #supabase

All tables in the `public` schema have **RLS enabled**. All policies are **PERMISSIVE** and apply to the `public` role.

## advisor_profiles
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_profile` | ALL | `auth.uid() = user_id` | Users can only read/write their own profile |

## chat_conversations
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `Users can create own conversations` | INSERT | `auth.uid() = user_id` (with_check) | Users can only create conversations for themselves |
| `Users can view own conversations` | SELECT | `auth.uid() = user_id` | Users can only see their own conversations |
| `Users can update own conversations` | UPDATE | `auth.uid() = user_id` | Users can only edit their own conversations |
| `Users can delete own conversations` | DELETE | `auth.uid() = user_id` | Users can only delete their own conversations |

## chat_messages
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_chat` | ALL | `auth.uid() = user_id` | Users can only access their own messages |

## generation_outputs
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_outputs` | ALL | `auth.uid() = user_id` | Users can only access their own generation history |

## generation_logs
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_logs` | SELECT | `auth.uid() = user_id` | Users can only read their own usage logs |

## prompt_feedback
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_feedback` | ALL | `auth.uid() = user_id` | Users can only access their own feedback |

## prompts (Legacy)
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_prompts` | ALL | `toolkit_id IN (SELECT id FROM toolkits WHERE user_id = auth.uid())` | Indirect ownership via toolkit |

## template_versions
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `read_templates` | SELECT | `auth.uid() IS NOT NULL` | Any authenticated user can read template versions |

## toolkits (Legacy)
| Policy | Operation | Expression | Meaning |
|--------|-----------|------------|---------|
| `own_toolkits` | ALL | `auth.uid() = user_id` | Users can only access their own toolkits |

## Admin Bypass
The admin client (`lib/supabase/admin.ts`) uses `SUPABASE_SERVICE_ROLE_KEY` which **bypasses all RLS policies**. Used for:
- `/api/admin/metrics` — Reading all user data for analytics
- `/api/admin/track-login` — Writing login events
- `handle_new_user()` trigger — SECURITY DEFINER function

## Security Notes
- All user-data tables enforce `auth.uid() = user_id`
- No cross-user data access is possible through the public API
- The `generation_logs` table only allows SELECT (not INSERT/UPDATE/DELETE via RLS — inserts happen server-side)
- Legacy tables (prompts, toolkits) have RLS but are unused

## Related Notes
- [[Schema]] — Table definitions
- [[Auth-Flow]] — How auth.uid() gets established
- [[User-Model]] — What data is protected
- [[API-Routes]] — Which routes use admin vs. user client
