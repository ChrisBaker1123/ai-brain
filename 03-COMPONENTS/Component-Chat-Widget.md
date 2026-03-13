# Component: Chat Widget

#component #feature

## File Path
`src/components/chat-widget.tsx` (263 lines)

## Purpose
Floating bottom-right chat bubble for quick AI Coach access.

## UI
- Gradient floating button (`from-blue-500 to-indigo-600`)
- Chat panel: fixed `bottom-20 md:bottom-6 right-4`, 360×480px
- Hidden on `/chat` page (to avoid duplicate)

## Behavior
- 3 predefined WIDGET_STARTERS prompts
- SSE streaming from `/api/chat`
- Auto-scroll, clear chat, Shift+Enter for newline

## Used On
- [[Component-Dashboard-Shell]] — Persistent across dashboard

## Related Notes
- [[Page-Chat]] — Full-page chat (widget hidden there)
- [[API-Routes]] — POST /api/chat
