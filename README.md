# ui-design-skill

A Claude skill for generating distinctive, production-grade frontend interfaces — built to avoid generic "AI slop" aesthetics and produce UI that actually looks designed.

## What it does

When activated, this skill guides Claude through building frontend components, pages, and applications with:

- A structured **design system** (tokens, typography, spacing, motion)
- **Three built-in themes** matched to different product categories
- Consistent use of **shadcn/ui** components and **Lucide React** icons
- Opinionated rules for every common component type (tables, cards, forms, dashboards, modals, etc.)

## Themes

### Analytical
> Dashboards, internal tools, data products, admin panels

Precise and warm. DM Sans typeface, warm stone neutrals with amber accents. Prioritises information density and scannability.

### Conversational
> AI assistants, document tools, knowledge bases, reading-heavy apps

Scholarly and calm. Crimson Pro serif typeface, parchment background with forest green primary. Prioritises legibility and trust.

### Vital
> Health, wellness, consumer products, onboarding flows

Organic and friendly. Quicksand typeface, clean white with fresh green accents. Prioritises warmth and approachability.

## How Claude picks a theme

1. **Project has a `CLAUDE.md`** — defers entirely to the project's own design system files
2. **No project files** — infers theme and stack from the request, confirms with you, then loads the matching reference files
3. **No signals at all** — goes full freestyle with detailed aesthetic guidance

Theme inference logic:
| Request type | Theme |
|---|---|
| Dashboards, data tools, admin panels | Analytical |
| AI assistants, docs, knowledge bases | Conversational |
| Health, wellness, consumer, onboarding | Vital |

Stack inference logic:
| Signals | Stack |
|---|---|
| Next.js, shadcn, App Router | Next.js + shadcn |
| React, Vite, `.jsx`/`.tsx`, no shadcn | React (no shadcn) |
| No signals | Next.js + shadcn (default) |

## Core rules (all themes)

- **Components**: Always shadcn/ui — never raw `<button>`, `<input>`, `<div className="card">` etc.
- **Icons**: Lucide React only · stroke only · `strokeWidth={1.5}` · `currentColor`
- **Tokens**: 3-layer architecture — primitives → semantic tokens → Tailwind classes. Never hardcode hex values in components.
- **Spacing**: 4px base scale — `4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 96px` only. No arbitrary values.
- **Motion**: `150ms ease-out` standard · `200ms ease-out` enter · `120ms ease-out` exit. No bouncing or springing.

## Repo structure

```
SKILL.md                          # Main skill definition (loaded by Claude)
references/
  core/PRINCIPLES.md              # Shared rules across all themes
  analytical/
    DESIGN.md                     # Analytical design system
    globals.css                   # Token values
  conversational/
    DESIGN.md                     # Conversational design system
    globals.css                   # Token values
  vital/
    DESIGN.md                     # Vital design system
    globals.css                   # Token values
```

## Branch strategy

| Branch | Purpose |
|---|---|
| `main` | Stable, released versions of the skill |
| `develop` | Active iteration and improvements |

Work on `develop` (or a `feature/` branch off it), then PR into `main` when ready.
