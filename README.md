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

### New project

The cleanest setup. Creates a Next.js project and configures everything automatically — shadcn, the right font, color tokens, and the design files Claude needs.

**1. Create a Next.js project**
```bash
npx create-next-app@latest my-project --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
cd my-project
```

**2. Run the setup for your chosen theme**

Analytical — dashboards, data tools, admin panels:
```bash
curl -s https://raw.githubusercontent.com/4rt3miy/ui-design-skill/main/themes/analytical/setup.sh | bash
```

Conversational — AI assistants, docs, knowledge bases:
```bash
curl -s https://raw.githubusercontent.com/4rt3miy/ui-design-skill/main/themes/conversational/setup.sh | bash
```

Vital — health, wellness, consumer apps:
```bash
curl -s https://raw.githubusercontent.com/4rt3miy/ui-design-skill/main/themes/vital/setup.sh | bash
```

**3. Open Claude Code and start prompting**
```bash
claude
```

Claude reads the design files automatically. Just describe what you want to build.

---

### Existing project

No setup needed. Install the skill once and it works in any project you open — Claude applies the design system automatically based on what you're building.

**1. Clone the skill once**
```bash
git clone https://github.com/4rt3miy/ui-design-skill.git ~/skills/ui-design-skill
```

**2. Launch Claude Code with the skill loaded**
```bash
claude --plugin-dir ~/skills/ui-design-skill
```

That's it. Works in any project, no files added to your repo.

**To avoid typing the flag every time**, add this to your shell config (`~/.zshrc` or `~/.bashrc`):
```bash
alias claude='claude --plugin-dir ~/skills/ui-design-skill'
```

Then just type `claude` as normal.
