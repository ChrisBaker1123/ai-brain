# Tech Stack

#project #tech

## Core Framework
| Technology | Version | Purpose |
|-----------|---------|---------|
| Next.js | 16.1.6 | React meta-framework, App Router |
| React | 19.2.3 | UI library |
| TypeScript | 5 | Type safety |
| Tailwind CSS | 4 | Utility-first styling (oklch color system) |

## Backend & Data
| Technology | Version | Purpose |
|-----------|---------|---------|
| Supabase | @supabase/supabase-js 2.99.0 | Auth + PostgreSQL + RLS |
| Supabase SSR | @supabase/ssr 0.9.0 | Server-side auth cookie management |
| Stripe | (via API) | Payment processing ($49.99/mo subscription) |

## AI
| Technology | Version | Purpose |
|-----------|---------|---------|
| @anthropic-ai/sdk | 0.78.0 | Claude API for AI Coach chatbot ONLY |
| Model (chat) | claude-sonnet-4-6 | AI Coach streaming responses |
| Model (generation) | claude-sonnet-4-5-20250514 | Content generation (currently unused in UI) |

**Important**: Templates are copy-paste, NOT AI-generated. The Claude API is used ONLY for the AI Coach chatbot.

## UI Components
| Technology | Version | Purpose |
|-----------|---------|---------|
| @base-ui/react | 1.2.0 | Headless UI primitives (NOT Radix) |
| shadcn/ui | 4.0.2 | Component registry (base-nova theme) |
| class-variance-authority | 0.7.1 | Component variant management |
| clsx | 2.1.1 | Conditional class composition |
| tailwind-merge | 3.5.0 | Tailwind class deduplication |

**Critical**: shadcn/ui uses `@base-ui/react` with `render` prop pattern, NOT `@radix-ui` with `asChild`.

## Animation
| Technology | Version | Purpose |
|-----------|---------|---------|
| framer-motion | 12.36.0 | Interactive animations, page transitions |
| Magic UI | Custom components | Shimmer, marquee, number ticker, blur fade, border beam |

## Utilities
| Technology | Version | Purpose |
|-----------|---------|---------|
| lucide-react | 0.577.0 | Icons |
| next-themes | 0.4.6 | Dark/light mode toggle |
| sonner | 2.0.7 | Toast notifications |
| recharts | 3.8.0 | Admin dashboard charts |

## Hosting & Deployment
| Technology | Purpose |
|-----------|---------|
| Vercel | Hosting, serverless functions, edge middleware |
| Supabase Cloud | PostgreSQL database, auth, RLS |

## Dev Dependencies
- `@tailwindcss/postcss` 4 — PostCSS integration
- `@types/node` 20, `@types/react` 19, `@types/react-dom` 19
- `eslint` 9, `eslint-config-next` 16.1.6

## Scripts
```bash
npm run dev    # Development server
npm run build  # Production build
npm run start  # Production start
npm run lint   # ESLint checks
```

## Related Notes
- [[Overview]] — Project overview
- [[Architecture]] — How it all fits together
- [[Design-System]] — Visual design with Tailwind
- [[Magic-UI-Components]] — Animation components
- [[Deployment]] — Deploy process
- [[Schema]] — Supabase database
