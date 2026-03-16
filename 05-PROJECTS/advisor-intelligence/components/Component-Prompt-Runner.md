# Component: Prompt Runner

#component #core

## File Path
`src/components/prompt-runner.tsx` (337 lines)

## Purpose
Modal for displaying, personalizing, and copying templates. The core UX component.

## Key Functions
- `buildAdvisorContext()` — Creates advisor profile context from Supabase data
- `buildReadyPrompt()` — Injects profile data + converts remaining `{{placeholders}}` to `[UPPERCASE INSTRUCTIONS]`

## Props
| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `prompt` | Prompt | Yes | Template data from prompts-data.json |
| `open` | boolean | Yes | Dialog visibility state |
| `onOpenChange` | (open: boolean) => void | Yes | Dialog toggle callback |
| `profile` | AdvisorProfile | No | User profile for auto-injection |

## Behavior
1. Opens as modal dialog
2. Auto-injects profile data (name, firm, type, credentials)
3. Converts remaining `{{placeholders}}` to `[UPPERCASE INSTRUCTIONS]`
4. Appends "BEFORE YOU SEND" section with field descriptions
5. Copy button → clipboard + toast + save to `generation_outputs`
6. "Open Copilot" + "Open ChatGPT" external link buttons
7. Shows [[Component-Template-Feedback]] after first copy
8. Loading skeleton while template prepares

## State Management
- `useState` for copy state, feedback visibility
- Profile data from parent component (Supabase query)

## Important Notes
- **Copilot-first**: Primary AI tool is Microsoft Copilot (copilot.microsoft.com)
- No API calls — everything is client-side clipboard copy
- No compliance sections in modal — just a single data safety note
- `document` prop shadows global `document` — use `window.document.body` for portal

## Used On
- [[Page-Toolkit]] — Template library

## Related Notes
- [[User-Model]] — Profile data that gets injected
- [[Architecture]] — Placeholder handling pattern
- [[Component-Document-Runner]] — Similar pattern for documents
