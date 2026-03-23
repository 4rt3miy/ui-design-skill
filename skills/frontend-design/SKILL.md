---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build, create, or design any frontend UI — including web components, pages, dashboards, apps, landing pages, React components, HTML/CSS layouts, admin panels, forms, or any visual interface. Also use when the user asks to generate marketing or PR collateral — social cards, announcement banners, LinkedIn images, presentation slides, or any static branded visual asset. Also use when the user says "use Ali", "use Zeroh", "use Blade Labs GRC", "use GRC", "switch design system", or "apply the design system". Generates creative, polished code and UI that avoids generic AI aesthetics.
license: Complete terms in LICENSE.txt
---

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design System Check

Before applying any aesthetic guidance, determine which of three paths applies:

**Path 1 — Project has a design system (repo context)**
If a `CLAUDE.md` exists in the project root, read it. It will reference a `DESIGN.md` and `PRINCIPLES.md`. Defer all typography, color, spacing, and aesthetic decisions to those files. Apply this skill for component structure and patterns only.

**Path 2 — No project files, theme and stack inferred**
If no `CLAUDE.md` exists, infer both the theme and the stack from the request, then surface both as a single confirmation line before generating anything.

**Brand inference:**
- Reading-heavy, AI assistants, document tools, knowledge bases, Shariah → **Ali**
- Health, wellness, consumer products, onboarding → **Zeroh**
- Dashboards, internal tools, data products, admin panels, compliance, GRC → **Blade Labs GRC**

If no brand signal is present and no `CLAUDE.md` exists, ask the user which brand to use before building.

**Stack inference:**
- Signals for **Next.js + shadcn**: mentions of Next.js, shadcn, App Router, `npx shadcn`, or the project has a `package.json` with these dependencies
- Signals for **React (no shadcn)**: mentions of React, Vite, CRA, `.jsx`/`.tsx` files, but no shadcn dependency or explicit exclusion
- Default to **Next.js + shadcn** when no stack signal exists at all

When both are inferred, announce both together before generating:

> *"Going with **Blade Labs GRC** + **React (no shadcn)** — data dashboard, no shadcn detected. Good?"*

If only brand is clear but stack is ambiguous, ask once alongside the brand confirmation:

> *"Going with **Ali** for this. Are you using Next.js + shadcn or plain React?"*

Once confirmed (or if the user just continues prompting), load the bundled references for the chosen theme:
- `references/[theme]/DESIGN.md` — full design system
- `references/core/PRINCIPLES.md` — shared rules

Treat these exactly as on-disk files in Path 1. The `references/[theme]/globals.css` is also available if token values are needed.

**Design decisions in DESIGN.md are non-negotiable.** Never substitute, rationalize away, or override any typeface, color, spacing, or token — even if you believe a different choice would be better suited to the use case. If DESIGN.md specifies Crimson Pro, use Crimson Pro. If it specifies a parchment background, use it. Your aesthetic preferences do not apply in Path 1 or Path 2.

If the user corrects the theme or stack, switch immediately and reload before generating.

**Stack adaptation rules (tokens-only):**
When the stack is **React (no shadcn)**, apply all theme tokens, typography, spacing, and color decisions exactly as specified in `DESIGN.md` — but use raw HTML elements with Tailwind utility classes instead of shadcn components. Never import from `@/components/ui`. The design system still applies in full; only the component primitives change.

| shadcn | React (no shadcn) |
|---|---|
| `<Button>` | `<button className="...">` |
| `<Card>` | `<div className="...">` |
| `<Input>` | `<input className="...">` |
| `<Badge>` | `<span className="...">` |
| `<Table>` | `<table className="...">` |
| `<Dialog>` | Custom modal div with backdrop |

All token values (colors, radius, spacing) remain identical — only the element type changes.

**Path 3 — No design system, no theme signal**
Proceed with the full freestyle aesthetic guidance below.

---

## Design Thinking

Before coding, understand the context and commit to a BOLD aesthetic direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, etc. There are so many flavors to choose from. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work - the key is intentionality, not intensity.

Then implement working code (HTML/CSS/JS, React, Vue, etc.) that is:
- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail

## Frontend Aesthetics Guidelines

> **Path 3 only.** These guidelines apply only when no theme has been selected and no `CLAUDE.md` is present. In Path 1 and Path 2, all aesthetic decisions come from `DESIGN.md` — not from these guidelines.

Focus on:
- **Typography**: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics; unexpected, characterful font choices. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions. Use scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures that match the overall aesthetic. Apply creative forms like gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, decorative borders, custom cursors, and grain overlays.

NEVER use generic AI-generated aesthetics like overused font families (Inter, Roboto, Arial, system fonts), cliched color schemes (particularly purple gradients on white backgrounds), predictable layouts and component patterns, and cookie-cutter design that lacks context-specific character.

Interpret creatively and make unexpected choices that feel genuinely designed for the context. No design should be the same. Vary between light and dark themes, different fonts, different aesthetics. NEVER converge on common choices (Space Grotesk, for example) across generations.

**IMPORTANT**: Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations and effects. Minimalist or refined designs need restraint, precision, and careful attention to spacing, typography, and subtle details. Elegance comes from executing the vision well.

Remember: Claude is capable of extraordinary creative work. Don't hold back, show what can truly be created when thinking outside the box and committing fully to a distinctive vision.

---

## Collateral & Static Branded Assets

When the request is for a **standalone visual** rather than a UI component or app page — social cards, announcement banners, LinkedIn images, event posters, PR assets — output a **single self-contained HTML file** with no external dependencies except Google Fonts.

**Rules for collateral output:**
- Skip the stack confirmation (no Next.js / shadcn question — it's always plain HTML)
- Still confirm the brand: *"Going with **Blade Labs GRC** for this announcement card. Good?"*
- Inline all CSS as a `<style>` block — no external stylesheets
- Use Google Fonts CDN for the brand typeface
- Inline the `Logo.svg` directly — do not use `<img src>` for the logo
- Apply the brand's exact tokens: primary color, background, typography scale
- Output at the requested dimensions via a fixed-size wrapper (e.g. `width:1200px; height:627px` for LinkedIn)
- The file must open directly in Chrome with no build step

**Common collateral sizes:**
| Format | Dimensions |
|---|---|
| LinkedIn post image | 1200 × 627px |
| Twitter/X card | 1200 × 675px |
| Instagram square | 1080 × 1080px |
| Presentation slide | 1920 × 1080px |
| Email banner | 600 × 200px |

**Figma handoff:** Users with the Figma MCP plugin can push the rendered HTML directly to Figma for final edits and export.

---

## Component Patterns

Different component types have different design priorities. Apply the aesthetic guidelines above, but also follow the component-specific principles below. When building a complex page, identify which component types are present and apply the relevant guidance to each.

### Hero Sections
The hero is the first impression — it must be immediate and visceral. The single most important principle: **one dominant visual idea**. A hero that tries to do too much (big text + illustration + animation + form + badges) collapses into noise. Pick the anchor — whether that's a typographic statement, a full-bleed image, a cinematic video, or a bold geometric shape — and let everything else serve it. Hierarchy should be unmistakable at a glance: headline, then subhead, then CTA, with enough breathing room that the eye knows exactly where to go. CTAs must feel consequential — size, contrast, and placement should make the primary action feel inevitable, not optional. Avoid hero sections that feel like templates: centered text, gradient blob behind it, two buttons. Push the layout off-center, overlap elements, break the grid.

### Navigation
Nav design is about trust and orientation: the user should always know where they are and feel confident they can get anywhere. For top navs, restraint is almost always right — too many items creates paralysis. If there are more than 6-7 items, group or condense. The active/current state must be unmistakable, not a subtle color shift that requires squinting. Mobile nav (hamburger menus, drawers, bottom bars) is where most implementations fall apart: ensure tap targets are large (min 44px), transitions are smooth and feel native, and the close/dismiss action is obvious. Sticky navs should earn their screen real estate — if the nav isn't useful while scrolling (no section links, no persistent actions), don't make it sticky. Avoid navs that look like every SaaS product: logo left, links center, "Sign Up" button right, all in the same weightless sans-serif.

### Forms
Forms are where users do work — the design job is to make that work feel effortless and trustworthy. Every field needs a clear label (not just placeholder text, which disappears on focus and fails accessibility). Group related fields visually; a form that's one long undifferentiated column feels like a survey. Validation feedback must be immediate, specific, and kind — "Invalid email" is less helpful than "Check the format: name@example.com". Error states should be visually distinct (color + icon, not color alone) and positioned close to the offending field. The submit button should reflect state: idle, loading, success, error — never leave the user wondering if their click registered. For multi-step forms, always show progress. Style-wise: forms reward restraint — the aesthetic should support focus, not distract. Custom-styled inputs (dropdowns, checkboxes, toggles) are high-impact but must remain functional and accessible.

### Data Tables
Tables present dense information — the design job is to make that density scannable, not overwhelming. Zebra striping or sufficient row padding (never both — they fight each other) are the two main tools for row separation. Column alignment is semantic: numbers right-align (so decimal points line up), text left-aligns, status indicators center. Sortable columns need clear affordance (icon + hover state) and must show current sort direction. For wide tables, consider freezing the first column on horizontal scroll rather than shrinking everything to illegibility. Empty states, loading states, and error states all need designs — a blank table with no explanation is a dead end. Avoid the default browser table aesthetic at all costs: it signals "unfinished". Consider whether a table is even the right component — if there are fewer than 3-4 columns, a card list often reads better.

### Cards & Grids
Cards are containers for repeatable content — their power is in consistency and scannability. The cardinal rule: **every card in a set must have the same structure**. Mixed-height cards in a grid (one has an image, one doesn't; one has a long title, one has a short one) create visual chaos. Use CSS Grid with `align-items: stretch` so cards fill their cell, and pin the CTA/action to the card's bottom so it's always in the same place. The grid gap and card padding should be proportional — a tight gap with generous internal padding, or a generous gap with tighter internal padding, both work; mismatched proportions look accidental. Card hover states should feel responsive and physical: a subtle lift (translateY + shadow increase) is reliable; overly complex hover animations distract from the content. For editorial or portfolio grids, a masonry or asymmetric layout can be stunning — but only if all the cards have consistent enough content to support it.

### Dashboards
Dashboards are about signal-to-noise ratio. The user's job is to extract insight fast — every design decision should serve that goal or get out of the way. Establish a clear visual hierarchy for metrics: primary KPIs (large, immediate), secondary metrics (medium, supporting), detail tables (compact, explorable). Color in dashboards is functional, not decorative — use it to encode meaning (status, trend direction, category) consistently throughout. Don't use the same green for both "success" and "revenue" in the same dashboard. Charts must be titled, labeled, and legible without a legend where possible; if a legend is necessary, place it close to the data. Sidebar navigation for dashboards should be compact and utility-focused — this is not a marketing page. The aesthetic should feel calm and professional: a maximalist hero treatment would be deeply wrong here. Aim for density that feels controlled, not cluttered.

### Modals & Overlays
Modals interrupt — that interruption must be justified and resolved quickly. They work for confirmations, focused forms, and detail views; they fail for complex multi-step flows or large amounts of content (use a drawer or new page instead). The backdrop should dim the page enough to establish focus (0.4–0.6 opacity dark overlay) without making the modal feel like it's floating in void. Close affordance must be immediate: an × in the top-right corner is the universal convention — don't be clever with it. Trap focus inside the modal for keyboard users. The modal's internal layout follows normal design rules, but with extra attention to padding — modals that feel cramped are claustrophobic; modals with generous padding feel considered. Animation: modals should enter with a subtle scale + fade (not a dramatic slide from off-screen), and exit quickly — the exit animation is the last thing the user sees before returning to their context.

### Empty, Loading & Error States
These three states are the most commonly neglected in frontend work, and the most visible when they're wrong. **Every component that fetches data needs all three states designed.** Loading states: use skeleton screens instead of spinners for content that has a known shape (cards, tables, profiles) — they set expectations and feel faster. Spinners are fine for actions (button click, form submit). Empty states: never show a blank area with no explanation. An empty state should tell the user what belongs here, why it's empty, and what they can do about it — and it should have a personality that fits the overall aesthetic. Error states: be specific about what went wrong and what the user can do (retry, contact support, go back). "Something went wrong" with no action is an apology, not a design. Style all three states with the same care as the happy path — they're part of the product.

---

## Brand Assets

Every brand ships two SVG files. **Always use these — never create placeholder logos or inline text as a logo substitute.**

| Brand | Logo (wordmark) | Icon (mark) |
|---|---|---|
| Ali | `themes/ali/assets/Logo.svg` | `themes/ali/assets/Icon.svg` |
| Zeroh | `themes/zeroh/assets/Logo.svg` | `themes/zeroh/assets/Icon.svg` |
| Blade Labs GRC | `themes/grc/assets/Logo.svg` | `themes/grc/assets/Icon.svg` |

**When to use each:**
- `Logo.svg` — full wordmark. Use in nav bars, page headers, login screens, marketing surfaces.
- `Icon.svg` — compact mark. Use for favicons, avatar slots, mobile nav, small contexts (≤32px).

**Critical: `currentColor` fill pattern**

All SVG paths use `fill="currentColor"`. This means the SVG color is controlled entirely by the CSS `color` property of its container — **no SVG edits needed when the color changes**.

```jsx
// React: inline SVG inherits color from parent
<div style={{ color: 'var(--primary)' }}>
  {/* paste SVG here — it renders in --primary */}
</div>

// To show on dark surface:
<div style={{ color: '#ffffff' }}>
  {/* same SVG — now renders white */}
</div>

// Tailwind:
<div className="text-primary">
  {/* SVG renders in brand primary */}
</div>
```

**In Next.js projects:** After `setup.sh` runs, assets are copied to `public/brand/`. Reference them as:
- `/brand/Logo.svg` — for `<img src>` or CSS `url()`
- Import and inline for `currentColor` control (recommended)

**Never** hardcode a hex color directly on the SVG element. Always control color through CSS `color` on the wrapper.

**Minimum sizes:** Logo ≥ 80px wide · Icon ≥ 16px · Icon typical UI size 32px

---

## Bundled References

Load these when operating in Path 2 (theme specified, no project files present).

| File | When to read |
|---|---|
| `references/core/PRINCIPLES.md` | Always, for any theme — shared rules |
| `references/ali/DESIGN.md` | Ali design system — typography, color, components |
| `references/ali/globals.css` | Ali token values |
| `references/zeroh/DESIGN.md` | Zeroh design system — typography, color, components |
| `references/zeroh/globals.css` | Zeroh token values |
| `references/grc/DESIGN.md` | Blade Labs GRC design system — typography, color, components |
| `references/grc/globals.css` | Blade Labs GRC token values |
| `themes/ali/assets/` | Ali brand SVGs (Logo.svg, Icon.svg) |
| `themes/zeroh/assets/` | Zeroh brand SVGs (Logo.svg, Icon.svg) |
| `themes/grc/assets/` | Blade Labs GRC brand SVGs (Logo.svg, Icon.svg) |
