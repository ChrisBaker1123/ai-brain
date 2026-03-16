---
type: decision
title: "Remove 13 analysis templates that overlap with existing systems"
status: active
created: 2026-03-16
updated: 2026-03-16
domain: product
decided: 2026-03-14
rationale: "Templates for functions covered by dedicated software hurt credibility"
derived_from:
  - "[[gap-filler-positioning]]"
---

## Decision
Remove 13 templates: Estate Tax Exposure Analysis, Roth Conversion Analysis, Tax-Loss Harvesting Review, Social Security Optimization, Retirement Income Withdrawal, Retirement Readiness Assessment, Complex Tax Analyzer, Comprehensive Retirement Review, Multi-Gen Wealth Transfer, Concentrated Stock Strategy, Divorce Financial Analysis, Pre-Retirement Review, Insurance Needs Deep Analysis.

## Context
A Morgan Stanley advisor would never trust AI for estate tax numbers. Every planning platform already has Roth conversion analysis. These templates signal we don't understand the advisor world.

## Rationale
The net result is positive: 61 → 68 templates after adding 19 high-value gap-filler templates. Educational versions of removed concepts (Roth Conversion Explainer, Social Security Options Explainer) remain in Client Education.

## Implications
- Template count changes but net increases
- 3 categories eliminated (Tax Planning, Retirement Planning, Deep Analysis)
- prompts-data.json needs updating

## Related
- [[Product-Strategy-Pivot]]
- [[2026-03-pivot-to-gap-filler]]
