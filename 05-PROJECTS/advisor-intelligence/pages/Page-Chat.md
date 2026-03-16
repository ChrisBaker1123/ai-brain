# Page: AI Coach (Chat)

#page #dashboard #ai

## Route
`/chat` — Protected

## Purpose
Full-page AI Coach chatbot. Streaming conversations with Claude.

## Layout
[[Component-Dashboard-Shell]]

## Content (580 lines)
- Sidebar: Conversation history list
- Main: Message thread with user/assistant bubbles
- Input: Textarea with Shift+Enter for newline
- 3 predefined quick-start prompts
- Clear conversation button
- Streaming via SSE from `/api/chat`

## Technical Details
- **Model**: claude-sonnet-4-6
- **System prompt**: Built from advisor profile + compliance rules via `buildSystemPrompt()`
- **Streaming**: Server-Sent Events
- **Persistence**: `chat_messages` + `chat_conversations` tables
- **Session caching**: sessionStorage
- **Rate limit**: Daily (currently 999999 = unlimited)

## Supabase Dependencies
- SELECT/INSERT on `chat_conversations`
- INSERT on `chat_messages`
- SELECT on `advisor_profiles` (system prompt context)

## Related Notes
- [[API-Routes]] — POST /api/chat
- [[Component-Chat-Widget]] — Floating mini-chat (hidden on this page)
- [[User-Model]] — Profile data in system prompt
- [[Schema]] — chat_messages, chat_conversations tables
