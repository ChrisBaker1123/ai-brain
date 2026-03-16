# Component: Crisp Chat

#component #integration

## File Path
`src/components/crisp-chat.tsx` (32 lines)

## Purpose
Crisp customer support chat widget loader.

## Notes
- Initializes `window.$crisp` and `CRISP_WEBSITE_ID`
- Script from https://client.crisp.chat/l.js
- Only loads if `NEXT_PUBLIC_CRISP_WEBSITE_ID` env var is set
- **Status**: Not currently active (env var not set)

## Used On
- Root layout (`app/layout.tsx`)

## Related Notes
- [[Deployment]] — Env var configuration
