# Component: Page Guide

#component

## File Path
`src/components/page-guide.tsx` (87 lines)

## Purpose
Per-page onboarding overlay. Shows guide on first visit, then collapses to "How to use this page" button.

## Props
- `steps` — Array of guide steps
- `storageKey` — localStorage key for tracking seen state

## UI
- Full guide on first visit
- Collapsed button after that
- Steps in 3-column grid

## Used On
Various dashboard pages for contextual help
