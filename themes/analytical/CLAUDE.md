# Design System

This project uses the **Analytical** theme.

## Before any UI work

Read these two files first — they define all design decisions:
- `docs/DESIGN.md` — typography, colors, components, spacing
- `docs/PRINCIPLES.md` — shared rules for all themes

## Non-negotiables

- Typeface: **DM Sans** — never substitute for another font
- Background: `bg-background` (warm off-white #F5F3F0)
- Primary: `bg-primary` (amber-brown #92400E)
- Components: shadcn/ui only — never raw HTML elements
- Icons: Lucide React only, `strokeWidth={1.5}`
- Tokens: semantic only — never raw hex values in components

## Stack

Next.js App Router · TypeScript · Tailwind CSS v4 · shadcn/ui · Lucide React
