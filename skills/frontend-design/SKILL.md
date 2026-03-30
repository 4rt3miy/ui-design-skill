---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build, create, or design any frontend UI — including web components, pages, dashboards, apps, landing pages, React components, HTML/CSS layouts, admin panels, forms, or any visual interface. Also use when the user asks to generate marketing or PR collateral — social cards, announcement banners, LinkedIn images, presentation slides, or any static branded visual asset. Also use when the user says "use Ali", "use Zeroh GRC", "use Blade Labs Corporate", "use GRC", "switch design system", or "apply the design system". Generates creative, polished code and UI that avoids generic AI aesthetics.
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
- Health, wellness, consumer products, onboarding → **Zeroh GRC**
- Dashboards, internal tools, data products, admin panels, compliance, GRC → **Blade Labs Corporate**

If no brand signal is present and no `CLAUDE.md` exists, ask the user which brand to use before building.

**Stack inference:**
- Signals for **Next.js + shadcn**: mentions of Next.js, shadcn, App Router, `npx shadcn`, or the project has a `package.json` with these dependencies
- Signals for **React (no shadcn)**: mentions of React, Vite, CRA, `.jsx`/`.tsx` files, but no shadcn dependency or explicit exclusion
- Default to **Next.js + shadcn** when no stack signal exists at all

When both are inferred, announce both together before generating:

> *"Going with **Blade Labs Corporate** + **React (no shadcn)** — data dashboard, no shadcn detected. Good?"*

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
- Still confirm the brand: *"Going with **Blade Labs Corporate** for this announcement card. Good?"*
- Inline all CSS as a `<style>` block — no external stylesheets
- Use Google Fonts CDN for the brand typeface
- Inline the `Logo.svg` directly — do not use `<img src>` for the logo
- Apply the brand's exact tokens: primary color, background, typography scale, and `--brand-gradient` for marketing surfaces
- For announcement cards, social banners, and event posters — use `var(--brand-gradient)` as the hero background; use `var(--primary)` for accent text or secondary elements
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
**Brand gradient rule (all three themes):** Every theme ships a `--brand-gradient` token. On marketing pages — hero sections, landing page CTAs, announcement banners — use `background: var(--brand-gradient)` for the hero background or primary CTA. Never use the gradient on app UI buttons, dashboard components, or interactive elements inside a product; those always use `var(--primary)` solid. When building a landing page for any of the three themes, the hero CTA should use the gradient by default unless the design brief specifies otherwise.

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

Every brand ships two SVG files. **Always use these — never create placeholder logos, inline text substitutes, or recreate marks from scratch.**

| Brand | Logo (wordmark) | Icon (mark) |
|---|---|---|
| Ali | `themes/ali/assets/Logo.svg` | `themes/ali/assets/Icon.svg` |
| Zeroh GRC | `themes/zeroh/assets/Logo.svg` | `themes/zeroh/assets/Icon.svg` |
| Blade Labs Corporate | `themes/corporate/assets/Logo.svg` | `themes/corporate/assets/Icon.svg` |

### Logo hierarchy

Three variants — use the right one for the context:

| Variant | What it is | When to use |
|---|---|---|
| **Lockup** | Icon + Wordmark composed side-by-side | Nav bars, page headers, login screens, marketing heroes, collateral — the primary form |
| **Icon only** | The mark alone | Sidebar (collapsed state), mobile nav, favicon, avatar slots, any context ≤ 32px wide |
| **Wordmark only** | Text alone | Wide-but-short spaces where the icon cannot fit legibly (rare) |

The lockup is always the first choice when space allows. Only drop to Icon-only when the container genuinely cannot fit the wordmark.

### Color variants

Four variants — choose based on the background surface:

| Variant | When to use | How |
|---|---|---|
| **Brand gradient** | Marketing heroes, landing CTAs, announcement banners, collateral | CSS mask + `var(--brand-gradient)` |
| **Solid primary** | App UI on light backgrounds — nav, header, login, product pages | `color: var(--primary)` on container |
| **White** | On dark surfaces or on gradient backgrounds | `color: #ffffff` on container |
| **Foreground** | Monochrome contexts, print | `color: var(--foreground)` on container |

**On gradient backgrounds, always use the white variant.** Never place the gradient logo on a gradient background.

### Implementation: solid color (`currentColor`)

All SVG paths use `fill="currentColor"`. Color is controlled entirely by the CSS `color` property of the wrapper — no SVG edits needed:

```jsx
// App nav — solid primary
<div style={{ color: 'var(--primary)' }}>
  {/* inline SVG — renders in brand primary */}
</div>

// On dark or gradient surface — white
<div style={{ color: '#ffffff' }}>
  {/* same SVG — renders white */}
</div>

// Tailwind
<div className="text-primary">...</div>
```

### Implementation: gradient (CSS mask)

Use CSS `mask` to apply the brand gradient through the SVG shape. The SVG is referenced as a URL (not inlined), so it must be accessible at a public path. In Next.js projects `setup.sh` copies assets to `public/brand/`.

```jsx
// Gradient lockup — marketing hero
<div
  style={{
    background: 'var(--brand-gradient)',
    WebkitMask: "url('/brand/Logo.svg') no-repeat center / contain",
    mask: "url('/brand/Logo.svg') no-repeat center / contain",
    width: '200px',
    height: '42px',
  }}
/>

// Gradient icon — standalone mark
<div
  style={{
    background: 'var(--brand-gradient)',
    WebkitMask: "url('/brand/Icon.svg') no-repeat center / contain",
    mask: "url('/brand/Icon.svg') no-repeat center / contain",
    width: '40px',
    height: '40px',
  }}
/>
```

### Favicon

Use **Icon.svg** — never Logo.svg (too wide for square format). Always use a **solid background** — never transparent. Browser chrome (tabs, bookmarks, OS dock) has unpredictable backgrounds; a transparent favicon becomes invisible on matching surfaces.

```html
<!-- favicon.svg: Icon on solid brand-primary background -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 36 36">
  <rect width="36" height="36" rx="8" fill="[brand-primary]"/>
  <!-- paste Icon.svg paths here with fill="white" -->
</svg>

<!-- In <head> -->
<link rel="icon" type="image/svg+xml" href="/brand/favicon.svg" />
<link rel="apple-touch-icon" sizes="180x180" href="/brand/apple-touch-icon.png" />
```

Per-brand favicon colors:

| Brand | Background | Icon color |
|---|---|---|
| Ali | `#1F5B46` (forest green) | `#ffffff` |
| Zeroh GRC | `#009966` (deep green) | `#ffffff` |
| Blade Labs Corporate | `#4f39f6` (indigo) | `#ffffff` |

### Minimum sizes

| Variant | Minimum | Typical |
|---|---|---|
| Lockup (icon + wordmark) | 120px wide | 160–200px |
| Icon | 16px | 24px nav · 32px UI |
| Favicon | 16px | 32px |

### Ali — signature lockup (special case)

Ali has **two separate colour systems**: gold for the logo, forest green for the app UI. They never mix.

The primary Ali logo form is a composed lockup: **Icon with a 3-stop metallic gold gradient** + **Wordmark in flat solid gold**, always on a dark/black background. Use `--logo-gradient` and `--logo-solid` — never `--brand-gradient` (which is sage→forest green and belongs to marketing UI only).

```jsx
// Ali signature lockup — dark background
<div style={{ display: 'flex', alignItems: 'center', gap: '20px', background: '#0A0A0A' }}>
  {/* Icon — 3-stop gold gradient: gold-700 → gold-200 → gold-500 */}
  <div style={{
    background: 'var(--logo-gradient)',
    WebkitMask: "url('/brand/Icon.svg') no-repeat center / contain",
    mask: "url('/brand/Icon.svg') no-repeat center / contain",
    width: '52px', height: '52px',
  }} />
  {/* Wordmark — flat solid gold (gold-300) */}
  <div style={{
    background: 'var(--logo-solid)',
    WebkitMask: "url('/brand/Logo.svg') no-repeat center / contain",
    mask: "url('/brand/Logo.svg') no-repeat center / contain",
    width: '200px', height: '52px',
  }} />
</div>
```

| Token | Value | Role |
|---|---|---|
| `--logo-gradient` | `linear-gradient(to right, #70510A, #F0D599, #C38D11)` | Icon fill — gold-700 → gold-200 → gold-500 |
| `--logo-solid` | `#DCB868` (`--gold-300`) | Wordmark fill — Figma-sourced anchor |

### Don'ts

- Never recreate, redraw, or substitute the logo with inline text
- Never add drop shadows, glows, outlines, or other effects to the SVG
- Never rotate or skew the logo
- Never stretch or distort proportions — always preserve the SVG aspect ratio
- Never place the gradient logo variant on a gradient background — use white on gradients
- Never use a transparent background for favicons
- Never use `Logo.svg` as a favicon — it is a wide wordmark, not a square mark
- Never hardcode a color directly on the SVG element — always control via CSS `color` on the wrapper
- **Ali only**: Never use `var(--brand-gradient)` on the Ali logo — the logo uses `var(--logo-gradient)` gold, not the green UI gradient

---

## Bundled References

Load these when operating in Path 2 (theme specified, no project files present).

| File | When to read |
|---|---|
| `references/core/PRINCIPLES.md` | Always, for any theme — shared rules |
| `references/ali/DESIGN.md` | Ali design system — typography, color, components |
| `references/ali/globals.css` | Ali token values |
| `references/zeroh/DESIGN.md` | Zeroh GRC design system — typography, color, components |
| `references/zeroh/globals.css` | Zeroh GRC token values |
| `references/corporate/DESIGN.md` | Blade Labs Corporate design system — typography, color, components |
| `references/corporate/globals.css` | Blade Labs Corporate token values |
| `themes/ali/assets/` | Ali brand SVGs (Logo.svg, Icon.svg) |
| `themes/zeroh/assets/` | Zeroh GRC brand SVGs (Logo.svg, Icon.svg) |
| `themes/corporate/assets/` | Blade Labs Corporate brand SVGs (Logo.svg, Icon.svg) |
