# Auth Flow

#database #auth

## Signup Flow
1. User visits `/login` and clicks "Sign up free"
2. Enters email + password (password strength validation in UI)
3. `supabase.auth.signUp()` creates row in `auth.users`
4. **Trigger fires**: `on_auth_user_created` → `handle_new_user()` (SECURITY DEFINER)
5. `handle_new_user()` inserts a bare row into `advisor_profiles` with just `user_id`
6. User redirected to `/profile` for onboarding

## Onboarding Flow (profile/page.tsx)
1. **Screen 1**: Full name, firm type, AUM range, specialties, pain points
2. **Screen 2**: Tone preference (formal / professional_warm / conversational) with live preview
3. **Confirmation screen**: Summary of choices, option to skip
4. Supabase `advisor_profiles` updated via RLS-protected UPDATE
5. Redirect to `/subscribe` (paywall) or `/dashboard`

## Login Flow
1. User visits `/login`, enters email + password
2. `supabase.auth.signInWithPassword()` authenticates
3. Session cookie set via `@supabase/ssr`
4. Login tracked: POST to `/api/admin/track-login` (inserts into `user_login_events`)
5. Redirect to `/dashboard`

## Google OAuth (Not Yet Configured)
1. User clicks "Sign in with Google" button on `/login`
2. Redirects to Google OAuth consent screen
3. Callback to `/callback/page.tsx`
4. `exchangeCodeForSession()` (NOT `onAuthStateChange`)
5. Session established, redirect to `/profile` or `/dashboard`
6. **Status**: Button exists in UI but `NEXT_PUBLIC_SUPABASE_GOOGLE_CLIENT_ID` not set

## Session Management
- **Library**: `@supabase/ssr` manages httpOnly cookies
- **Middleware**: Every request passes through `middleware.ts` → `updateSession()`
- `updateSession()` refreshes the Supabase auth token via cookies
- **Server components**: Use `createServerClient()` from `lib/supabase/server.ts`
- **Client components**: Use `createBrowserClient()` from `lib/supabase/client.ts`

## Password Reset
1. User clicks "Forgot password?" on `/login`
2. Redirected to `/reset-password`
3. Step 1: Enter email → `supabase.auth.resetPasswordForEmail()`
4. Step 2: Enter verification code from email
5. Step 3: Enter new password with strength validation
6. Success → redirect to `/login`

## Protected Route Logic
- `middleware.ts` checks session for all non-public routes
- Public routes: `/`, `/login`, `/pricing`, `/terms`, `/privacy`, `/book`, `/about`, `/trust`, `/preview`, `/compare`, `/reset-password`
- API routes and `/callback` bypass redirect
- Missing session → redirect to `/login`

## Admin Authentication
- Checked in `/api/admin/metrics/route.ts` and admin layout
- Compares user email against `ADMIN_EMAIL` env var
- OR compares user ID against `ADMIN_USER_ID` env var
- Admin bypasses paywall

## Supabase Client Types
| Client | File | Context | RLS |
|--------|------|---------|-----|
| Browser | `lib/supabase/client.ts` | Client components | Yes |
| Server | `lib/supabase/server.ts` | Server components, API routes | Yes |
| Admin | `lib/supabase/admin.ts` | Admin operations | **No** (bypasses RLS) |

## Functions
```sql
-- Auto-creates profile on signup (SECURITY DEFINER = runs as owner, not caller)
CREATE FUNCTION handle_new_user() RETURNS trigger AS $$
BEGIN
  INSERT INTO public.advisor_profiles (user_id) VALUES (NEW.id);
  RETURN NEW;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

-- Auto-updates updated_at timestamp
CREATE FUNCTION update_updated_at() RETURNS trigger AS $$
BEGIN
  NEW.updated_at = now();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

## Triggers
| Trigger | Table | Event | Action |
|---------|-------|-------|--------|
| `on_auth_user_created` | auth.users | AFTER INSERT | `handle_new_user()` |
| `set_updated_at` | advisor_profiles | BEFORE UPDATE | `update_updated_at()` |

## Related Notes
- [[Schema]] — Full database schema
- [[RLS-Policies]] — Row-level security
- [[User-Model]] — What profile data is collected
- [[Page-Login]] — Login page UI
- [[Page-Profile]] — Onboarding UI
- [[Deployment]] — Required env vars for auth
