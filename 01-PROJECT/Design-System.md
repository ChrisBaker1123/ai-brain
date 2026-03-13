# Design System

#project #design

## Color System (oklch)

### Light Mode
| Variable | Value | Usage |
|----------|-------|-------|
| `--background` | `oklch(0.985 0.002 80)` | Page backgrounds (warm neutral) |
| `--foreground` | `oklch(0.175 0.008 286)` | Primary text |
| `--primary` | `oklch(0.528 0.243 268)` | Blue accent (#3152f4), CTAs, links |
| `--primary-foreground` | `oklch(0.985 0.002 80)` | Text on primary buttons |
| `--muted` | `oklch(0.955 0.003 80)` | Subtle backgrounds |
| `--muted-foreground` | `oklch(0.450 0.010 286)` | Secondary text (darkened for readability) |
| `--card` | `oklch(1 0 0)` | Card backgrounds |
| `--border` | `oklch(0.912 0.004 286)` | Borders |
| `--accent` | `oklch(0.955 0.003 80)` | Accent backgrounds |
| `--destructive` | `oklch(0.577 0.245 27.325)` | Error/danger red |

### Dark Mode
| Variable | Value | Usage |
|----------|-------|-------|
| `--background` | `oklch(0.154 0.010 286)` | Deep dark backgrounds |
| `--foreground` | `oklch(0.985 0.002 286)` | Light text |
| `--primary` | `oklch(0.623 0.214 268)` | Lighter blue for dark mode |
| `--muted` | `oklch(0.212 0.014 286)` | Dark muted backgrounds |
| `--muted-foreground` | `oklch(0.680 0.010 286)` | Light secondary text |

### Design Philosophy
- **Warm neutral hue 80** (NOT blue hue 264) for backgrounds — finance-appropriate
- **Blue primary** for trust and professionalism
- **No blue-tinted backgrounds** — they feel cold/tech; warm neutrals feel approachable
- Inspired by World Labs aesthetic (premium, clean, minimal)

## Typography
| Element | Font | Weight | Notes |
|---------|------|--------|-------|
| Body | Plus Jakarta Sans | 400, 500, 600, 700 | Swapped from Geist for distinctiveness |
| Headings | Plus Jakarta Sans | 600, 700 | Same family, bolder weights |
| Code | System monospace | 400 | Minimal code display |

## Spacing & Layout
- Container max-width: responsive (Tailwind defaults)
- Sidebar width: `lg:w-64` (fixed at lg breakpoint)
- Card padding: varies by size prop (default, sm)
- Section spacing: `py-16` to `py-24` on landing page sections

## Border Radius
- Buttons: `rounded-md` (default), `rounded-full` (pills)
- Cards: `rounded-xl`
- Inputs: `rounded-md`
- Modals: `rounded-xl`
- Avatars: `rounded-full`

## Shadows
- Cards: subtle shadow via `shadow-sm` or border only
- Modals: `shadow-lg` on overlay
- Floating elements: `shadow-xl`

## Gradients
| Usage | Gradient |
|-------|----------|
| AI Coach avatar/CTAs | `from-blue-500 to-indigo-600` |
| Hero text accent | Blue primary color (not gradient) |
| Chat widget button | `from-blue-500 to-indigo-600` |
| Landing page CTA sections | `from-primary/5 via-background to-background` |

## Animation Patterns
| Pattern | Technology | Details |
|---------|-----------|---------|
| Page section reveals | Framer Motion (BlurFade) | `duration: 0.5s`, `yOffset: 6`, staggered delays |
| Number counters | Framer Motion (NumberTicker) | Spring physics, `useMotionValue` + `useSpring` |
| Marquee scrolling | CSS animation | `marquee` keyframe, pauseOnHover |
| Shimmer buttons | CSS animation | `shimmer-slide` + `spin-around` keyframes |
| Border beam | Framer Motion | Gradient beam along element border |
| Shiny text | CSS animation | Background gradient clip with shimmer |
| Fade up | CSS animation | `fade-up` keyframe for landing sections |

## Responsive Breakpoints
| Breakpoint | Behavior |
|-----------|----------|
| < md (768px) | Mobile: bottom nav, hamburger menu, stacked layouts |
| md–lg | Tablet: sidebar collapsible, responsive grids |
| ≥ lg (1024px) | Desktop: fixed sidebar, multi-column layouts |

## Related Notes
- [[Magic-UI-Components]] — Animation component details
- [[Overview]] — Project context
- [[Tech-Stack]] — Tailwind CSS v4, Framer Motion versions
- [[Page-Landing]] — Where most design patterns are showcased
