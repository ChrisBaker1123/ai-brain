# Page: Login / Signup

#page #auth

## Route
`/login` — Public

## Purpose
Authentication entry point. Handles both login and signup.

## Layout
Centered card on warm neutral/gradient background

## Elements
- Logo + "Advisor Intelligence" brand text
- "Sign in to your toolkit" heading
- Email + password fields
- "Forgot password?" link → /reset-password
- "Sign In" button (blue, full-width)
- "Don't have an account? Sign up free" toggle
- Legal text: Terms + Privacy links
- "Back to homepage" link
- **No Google OAuth button visible** (env var not configured)

## Signup Mode
- Password strength validation in UI
- Creates auth.users row → triggers handle_new_user()
- Redirects to /profile for onboarding

## Known Issues
- Console warning about missing autocomplete attributes on input elements
- Google OAuth button hidden when NEXT_PUBLIC_SUPABASE_GOOGLE_CLIENT_ID not set

## Components Used
Standard HTML form elements, no shadcn dialog

## Supabase Dependencies
- `supabase.auth.signInWithPassword()` — Login
- `supabase.auth.signUp()` — Registration

## Auth Requirements
Public (redirects to dashboard if already authenticated)

## SEO
- **Title**: "Advisor Intelligence | AI Toolkit for Financial Advisors"

## Related Notes
- [[Auth-Flow]] — Complete auth flow
- [[Page-Profile]] — Next step after signup
- [[Page-Reset-Password]] — Password recovery
