# Component: Site Tour

#component #feature

## File Path
`src/components/site-tour.tsx` (671 lines)

## Purpose
10-step interactive tutorial highlighting key features.

## Steps
1-10 steps with: id, target (CSS selector), navigateTo, title, content, detail, icon

## Technical
- `waitForElement()` — MutationObserver with 5s timeout
- `computePosition()` — Smart tooltip placement
- 4px blue glow highlight on target elements
- Progress bar + navigation buttons
- Auto-start on first dashboard visit
- Keyboard: Escape, ArrowLeft, ArrowRight, Enter
- Skips step if target element missing (prevents stuck overlay)

## Components
- `TakeTourButton` — Sidebar trigger
- `DashboardTourButton` — Header trigger

## Used On
- [[Component-Dashboard-Shell]] — Always available

## Related Notes
- [[Page-Dashboard]] — Auto-starts on first visit
