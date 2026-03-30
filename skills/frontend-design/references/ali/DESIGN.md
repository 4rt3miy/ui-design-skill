# Conversational — Design System

Scholarly, warm, reading-heavy. Every decision prioritises legibility, trust, and considered breathing room.

---

## Typography

Single typeface: **Crimson Pro** (serif). Weight and size alone define hierarchy.

| Role | Size | Weight | Usage |
|---|---|---|---|
| Display | 48px | 700 | Hero headers, page titles |
| Heading 1 | 30px | 600 | Section titles, modal headers |
| Heading 2 | 24px | 600 | Card headers, panel titles |
| Heading 3 | 20px | 600 | Sub-sections, widget titles |
| Body Large | 16px | 400 | Primary readable content |
| Body | 14px | 400 | Secondary content, descriptions |
| Label / UI | 13px | 500 | Navigation, badges, buttons |
| Caption | 12px | 400 | Timestamps, metadata, footnotes |

```tsx
// Font setup in layout.tsx
import { Crimson_Pro } from 'next/font/google'
const crimsonPro = Crimson_Pro({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-crimson',
})
```

---

## Colors

Always use semantic tokens. Never use primitive hex values in components.

| Token | Value | Usage |
|---|---|---|
| `bg-background` | #F7F6F3 | App background |
| `text-foreground` | #221D15 | Primary text, headings |
| `bg-primary` | #1F5B46 | Primary buttons, active states |
| `text-primary-foreground` | #F7F6F3 | Text on primary surfaces |
| `bg-muted` | #EFEDE8 | Chips, hover backgrounds |
| `text-muted-foreground` | #7D7669 | Secondary text, metadata |
| `bg-accent` | #F5EAD0 | Gold wash accent areas |
| `border-border` | #E2DED6 | Card outlines, dividers |
| `ring-ring` | #A1C4B7 | Focus rings |
| `text-destructive` | #DC2626 | Errors, critical states |

### Sidebar tokens
| Token | Usage |
|---|---|
| `bg-sidebar` | Sidebar background |
| `text-sidebar-foreground` | Sidebar text |
| `bg-sidebar-primary` | Active nav item |
| `bg-sidebar-accent` | Hover / selected state |
| `border-sidebar-border` | Sidebar dividers |

### Logo

| Variant | Context | Implementation |
|---|---|---|
| Lockup gradient | Marketing heroes, collateral, splash screens | CSS mask + `var(--brand-gradient)` |
| Lockup solid | App nav, headers, login | `color: var(--primary)` on wrapper |
| Lockup white | On dark or gradient backgrounds | `color: #ffffff` on wrapper |
| Icon only | Collapsed sidebar, mobile nav, ≤ 32px contexts | Same color rules as lockup |
| Favicon | Browser tab, bookmarks, app icon | Icon on `#1F5B46` solid background, white paths |

The gold-to-green gradient on the icon is the signature mark of Ali — use it on all premium marketing surfaces.

---

### Brand gradient

The gradient is the brand's signature on marketing surfaces. Use it on hero sections, landing page CTAs, and announcement banners. Use the solid primary for all app UI.

| Token | Value |
|---|---|
| `--brand-gradient` | `linear-gradient(to right, #6FA28F, #1F5B46)` |
| `--brand-gradient-start` | `#6FA28F` (sage green) |
| `--brand-gradient-end` | `#1F5B46` (forest green) |

```tsx
// Marketing CTA — use the gradient
<a style={{ background: 'var(--brand-gradient)' }} className="text-white px-6 py-3 rounded-lg">
  Explore Ali →
</a>

// App UI button — use solid primary
<Button>Primary Action</Button>
```

---

## Components

### Buttons
```tsx
// Primary — one per view maximum
<Button>Primary Action</Button>

// Secondary
<Button variant="outline">Secondary</Button>

// Tertiary / icon buttons, nav
<Button variant="ghost">Ghost</Button>

// Destructive only
<Button variant="destructive">Delete</Button>
```
Radius: `10px` · Padding: `8px 18px` · Weight: 600 primary, 500 secondary

### Cards
```tsx
<Card className="rounded-[18px] border border-border shadow-sm p-6 bg-card">
  <h3 className="text-lg font-semibold text-foreground">Title</h3>
  <p className="text-sm text-muted-foreground mt-1">Subtitle</p>
</Card>
```
Default: warm white surface · Tinted: `bg-accent` for active/selected states

### Badges
```tsx
<Badge variant="outline">Approved</Badge>
```
Pill shape · 12px 600 · Semantic background tints at 7–10% opacity

### Inputs
```tsx
<Input placeholder="Search..." className="h-[42px] rounded-[12px]" />
```
Height: `42px` · Radius: `12px` · Focus ring: primary at 8% opacity

### Page layout
```tsx
<div className="container mx-auto px-6 py-8">
  {/* content */}
</div>
```

---

## Spacing

| Value | Usage |
|---|---|
| 4px | Icon gap, tight inline |
| 8px | Tag padding, minor gap |
| 12px | Card inner gap, list items |
| 16px | Standard section gap |
| 24px | Card padding |
| 32px | Between components |
| 48px | Section vertical rhythm |

---

## Border Radius

| Value | Usage |
|---|---|
| 4px | Micro elements |
| 8px | Buttons |
| 10px | Inputs |
| 14px | Cards (small) |
| 18px | Cards (large) |
| Full | Badges, pills |

---

## Don'ts

- Never introduce a second typeface
- Never substitute Crimson Pro for another typeface — not Inter, not a sans-serif, not "something more suited to docs"
- Never use raw hex values in components
- Never use arbitrary Tailwind spacing values
- Never use filled icons
- Never use `ease-in-out` or `linear` transitions
- Never use raw `<button>` or `<input>` elements
- Never use gray-400 for text — fails contrast on parchment background
- Never use the brand gradient on app UI buttons, links, or interactive elements — gradient is for marketing surfaces only
