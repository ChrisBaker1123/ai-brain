# Page: Action Plans (Scenario to Plan)

#page #dashboard #feature

## Route
`/scenario-to-plan` — Protected

## Purpose
Multi-step action planning. Select a client scenario, fill intake fields, get a structured plan.

## Layout
[[Component-Dashboard-Shell]]

## Content (797 lines — second largest page)

### Scenario Selection (5 categories)
- Life Transitions (inheritance, divorce, career change, empty nest, windfall)
- Retirement (early retirement, RMD, Social Security)
- Business & Equity (equity comp, pre-IPO, business sale)
- Estate (multi-gen transfer, legacy, executor duties)
- Tax & Investment (tax-loss harvesting, bracket management, charitable)

### Intake Form
Dynamic fields per scenario (client name, amounts, asset types, emotional state, etc.)

### Plan Display (StepCard component)
- Objective, prompt (copy-paste ready), context, expected output
- Specialist referral flag, review checklist
- Collapsible design, copy as markdown

### Export
- `generatePlan()` converts `{{placeholders}}` to `[INSTRUCTIONS]`
- `exportPlanAsMarkdown()` for full plan export

## Data Source
- `lib/scenario-to-plan/scenarios-1-5.ts`
- `lib/scenario-to-plan/scenarios-6-10.ts`
- `lib/scenario-to-plan/scenarios-part2.ts`
- `lib/scenario-to-plan/types.ts` + `generators.ts`

## Supabase Dependencies
None — client-side only

## Related Notes
- [[Page-Dashboard]] — Sidebar link with "NEW" badge
- [[Page-Toolkit]] — Related templates referenced in plans
