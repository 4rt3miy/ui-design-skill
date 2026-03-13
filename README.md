# ui-design-skill

A Claude skill that gives every interface it builds a consistent, intentional design — so you never have to think about fonts, colors, or layout.

## Who this is for

You build prototypes and apps with Claude Code. You care about how things look but don't want to think about design decisions yourself. This skill handles all of that automatically, every time Claude builds something for you.

## What it does

When active, this skill gives Claude a complete design system to work from. Every component, page, and layout it generates follows consistent rules for typography, color, spacing, and motion. You never see any of that. You just get UI that looks like someone designed it.

- **Three built-in themes** matched to different product types
- Consistent components and icons across everything it builds

## Themes

There are three themes. Claude picks the right one based on what you're building — you can always tell it to switch.

### Analytical
> Dashboards, internal tools, data products, admin panels

Precise and warm. DM Sans typeface, warm stone neutrals with amber accents. Prioritises information density and scannability.

### Conversational
> AI assistants, document tools, knowledge bases, reading-heavy apps

Scholarly and calm. Crimson Pro serif typeface, parchment background with forest green primary. Prioritises legibility and trust.

### Vital
> Health, wellness, consumer products, onboarding flows

Organic and friendly. Quicksand typeface, clean white with fresh green accents. Prioritises warmth and approachability.

**How Claude picks:**

| What you're building | Theme |
|---|---|
| Dashboards, data tools, admin panels | Analytical |
| AI assistants, docs, knowledge bases | Conversational |
| Health, wellness, consumer, onboarding | Vital |

Claude will confirm before generating anything:
> *"Going with **Analytical** — data dashboard. Good?"*

Just say yes and it builds. If it picked wrong, tell it and it switches.

## Getting started

### Starting from scratch (most common)

Run these two commands once — they install the skill so it's available every time you open Claude Code.

```bash
# Save the skill somewhere permanent on your machine
git clone https://github.com/4rt3miy/ui-design-skill.git ~/skills/ui-design-skill
```

Then launch Claude Code like this:

```bash
claude --plugin-dir ~/skills/ui-design-skill
```

From now on, whenever you ask Claude to build UI, the design system is automatically applied. No config, no files to touch.

**To make this permanent** (so you never have to add the flag again), add one line to your shell config:

```bash
alias claude='claude --plugin-dir ~/skills/ui-design-skill'
```

After that, just type `claude` as normal.

---

### Starting from a template

[4rt3miy/design-system](https://github.com/4rt3miy/design-system) is a starter template with a theme already picked and everything pre-configured. Clone it to start a new project:

```bash
git clone https://github.com/4rt3miy/design-system.git my-project
cd my-project
./setup.sh
```

Then open Claude Code and start prompting. The design system is already in place — no extra steps.
