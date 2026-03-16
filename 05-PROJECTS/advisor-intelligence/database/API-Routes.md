# API Routes

#database #api

## Template & Content Routes

### POST /api/generate (Currently Unused)
- **Auth**: Supabase user required
- **Purpose**: AI-generate content from template (legacy — UI now uses copy-paste)
- **Body**: `{ promptTemplate, userInputs, promptId, promptTitle, category }`
- **Response**: `{ content, model, usage: { inputTokens, outputTokens, durationMs }, rateLimit: { remaining, limit } }`
- **Notes**: Rate-limited monthly. Calls `generateContent()` with Claude API. Saves to `generation_outputs`.

### POST /api/favorite
- **Auth**: Supabase user required
- **Purpose**: Toggle favorite status on a generation output
- **Body**: `{ outputId, favorited }`
- **Response**: Success/error
- **Table**: Updates `generation_outputs.is_favorited`

### POST /api/feedback
- **Auth**: Supabase user required
- **Purpose**: Submit thumbs up/down rating on a template
- **Body**: `{ promptId, promptTitle, category, rating ("up"|"down"), comment? }`
- **Response**: Success/error
- **Validation**: Comment max 5000 chars
- **Table**: Updates `generation_outputs` with `feedback_rating` and `feedback_comment`

## AI Coach Routes

### POST /api/chat
- **Auth**: Supabase user required
- **Purpose**: Stream AI Coach response
- **Body**: `{ messages: Array<{role, content}>, conversationId? }`
- **Validation**: Max 50 messages per conversation, 15,000 chars per message
- **Model**: `claude-sonnet-4-6`
- **Response**: Server-Sent Events (SSE) stream with text chunks
- **System prompt**: Built from advisor profile context + chatbot addendum
- **Side effects**: Non-blocking save to `chat_messages` table
- **Rate limit**: Daily chat message limit

### GET /api/chat/conversations
- **Auth**: Supabase user required
- **Purpose**: List user's chat conversations
- **Response**: Array of conversation summaries

### POST /api/chat/conversations
- **Auth**: Supabase user required
- **Purpose**: Create a new conversation
- **Response**: New conversation object

### GET /api/chat/conversations/[id]
- **Auth**: Supabase user required
- **Purpose**: Get conversation with messages
- **Response**: Full conversation with message history

## Admin Routes

### GET /api/admin/metrics
- **Auth**: ADMIN_EMAIL or ADMIN_USER_ID env var check
- **Client**: Admin client (bypasses RLS)
- **Purpose**: Complete analytics dashboard data
- **Response**: `{ overview, tierCounts, dailyActiveUsers, hourlyActivity, signupTimeline, generationsTimeline, categoryUsage, topTemplates, streakLeaderboard, recentSignups, recentLogins, allUsers }`
- **Notes**: ~344 lines of aggregation queries. Auto-polled every 5 min by admin dashboard.

### POST /api/admin/track-login
- **Auth**: Supabase user required
- **Purpose**: Record login event
- **Table**: Inserts into `user_login_events`
- **Notes**: Called from dashboard-shell on page load, debounced to 30 min

## Stripe Routes (Built but may not be active)

### POST /api/stripe/checkout
- **Purpose**: Create Stripe checkout session
- **Config**: 7-day trial, $49.99/mo, `allow_promotion_codes: true`

### POST /api/stripe/webhook
- **Purpose**: Handle Stripe webhook events
- **Events**: `checkout.session.completed`, `customer.subscription.updated`, `customer.subscription.deleted`
- **Status**: Needs `STRIPE_WEBHOOK_SECRET` env var configured

### POST /api/stripe/portal
- **Purpose**: Create Stripe billing portal session

## Rate Limiting
| Endpoint | Limit | Period |
|----------|-------|--------|
| /api/generate | 999999 | Monthly |
| /api/chat | 999999 | Daily |

All limits currently set to 999999 (effectively unlimited). Replace with Redis/Supabase for production.

## Related Notes
- [[Schema]] — Tables these routes query
- [[Auth-Flow]] — How authentication works
- [[RLS-Policies]] — Data access control
- [[Component-Prompt-Runner]] — Client-side template handling (replaces /api/generate)
- [[Component-Chat-Widget]] — Client for /api/chat
