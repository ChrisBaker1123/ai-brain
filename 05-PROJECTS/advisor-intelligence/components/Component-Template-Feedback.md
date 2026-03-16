# Component: Template Feedback

#component

## File Path
`src/components/template-feedback.tsx` (115 lines)

## Purpose
Thumbs up/down feedback widget shown after first template copy.

## Behavior
- Auto-submit on thumbs up
- Optional comment textarea on thumbs down
- POST to `/api/feedback`
- Animated fade-in/slide-in

## Used On
- [[Component-Prompt-Runner]] — After first copy

## Related Notes
- [[API-Routes]] — POST /api/feedback
