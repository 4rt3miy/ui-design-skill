# ui-design-skill

A Claude skill for generating distinctive, production-grade frontend interfaces — built to avoid generic "AI slop" aesthetics and produce UI that actually looks designed.

## Who this is for

You build prototypes and apps using Claude Code. You're not a developer, you don't pick UI frameworks, and you don't want to think about fonts, colors, or spacing. You just want what you build to look intentional.

This skill is the design layer that runs inside Claude Code so you never have to make those decisions yourself.

## What it does

When active, this skill gives Claude a complete design system to work from — so every component, page, and layout it generates follows consistent rules for typography, color, spacing, and motion. You never see any of that. You just get UI that looks like someone designed it.

- **Three built-in themes** matched to different product types
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

## Normal workflow (with repo setup)

If you're using a theme repo from [4rt3miy/design-system](https://github.com/4rt3miy/design-system), the flow is:

1. Clone the theme repo
2. Run `setup.sh` — it installs shadcn, copies `CLAUDE.md` + `DESIGN.md` into your project, configures fonts, and sets up `globals.css`
3. Open Claude Code: `claude`
4. Start prompting in plain language

Claude reads `CLAUDE.md` automatically on startup, loads the design system, and applies it to everything it builds. You never touch a token, never pick a font, never choose a color.

## What this skill fixes

When you work outside the repo flow — no `setup.sh` run, no `CLAUDE.md` in the project — Claude has nothing to defer to and starts making random UI choices. Different fonts every time, inconsistent colors, layouts that don't match.

This skill is the fallback. It's bundled inside Claude Code itself, so when Claude detects there's no design system in your project, it automatically loads a matching theme from the skill and applies the same consistent rules. Same quality output, no setup required.

## Add to any project

If you want this skill available in a project that doesn't use the `setup.sh` flow, do this once:

```bash
# 1. Clone the skill repo somewhere permanent on your machine
git clone https://github.com/4rt3miy/ui-design-skill.git ~/skills/ui-design-skill

# 2. Launch Claude Code with the skill loaded
claude --plugin-dir ~/skills/ui-design-skill
```

That's it. The skill is now active for that session in whatever project you're working on — no `CLAUDE.md`, no setup, no config. Claude will automatically apply the design system whenever you ask it to build UI.

**Tip:** Add an alias to your shell config so you never have to type the flag:
```bash
alias claude='claude --plugin-dir ~/skills/ui-design-skill'
```

---

## How Claude picks a theme

Claude reads your prompt and picks the closest match:

| Request type | Theme |
|---|---|
| Dashboards, data tools, admin panels | Analytical |
| AI assistants, docs, knowledge bases | Conversational |
| Health, wellness, consumer, onboarding | Vital |

It will confirm the theme before generating anything:
> *"Going with **Analytical** — data dashboard. Good?"*

Just say yes (or nothing) and it builds. If it picked wrong, tell it and it switches immediately.

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
