# Page: Reset Password

#page #auth

## Route
`/reset-password` — Public

## Flow (208 lines)
1. Email step → `supabase.auth.resetPasswordForEmail()`
2. Code verification from email
3. New password with strength validation
4. Success → redirect to `/login`

## Related Notes
- [[Auth-Flow]] — Part of auth system
- [[Page-Login]] — "Forgot password?" link
