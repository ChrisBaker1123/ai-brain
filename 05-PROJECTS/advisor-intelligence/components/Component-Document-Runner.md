# Component: Document Runner

#component #core

## File Path
`src/components/document-runner.tsx` (334 lines)

## Purpose
Modal for multi-page document templates with coaching overlays.

## Props
| Prop | Type | Required |
|------|------|----------|
| `document` | Document | Yes |
| `open` | boolean | Yes |
| `onOpenChange` | fn | Yes |
| `profile` | AdvisorProfile | No |

## Behavior
- First-time coaching guide (Sparkles icon, stored in localStorage `doc_runner_seen`)
- Tip section for using reasoning modes in AI tools
- Multi-page document context guidance
- Copy, Open Copilot, Open ChatGPT buttons
- Same placeholder → `[INSTRUCTIONS]` conversion as prompt-runner

## Bug Fixed
- `document` prop shadowed global `document` — fixed to use `window.document.body`

## Used On
- [[Page-Documents]] — Document Builder

## Related Notes
- [[Component-Prompt-Runner]] — Similar pattern
