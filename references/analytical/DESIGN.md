# Analytical — Design System

Precise, warm, data-first. Every decision prioritises information density, clarity, and quiet confidence. Warm enough to feel human — never clinical.

---

## Typography

Single typeface: **DM Sans** (contemporary geometric sans). Clean and neutral with just enough personality to avoid feeling sterile.

| Role | Size | Weight | Usage |
|---|---|---|---|
| Display | 32px | 700 | Page titles, hero metrics |
| Heading 1 | 24px | 600 | Section titles, panel headers |
| Heading 2 | 18px | 600 | Card headers, widget titles |
| Heading 3 | 15px | 600 | Sub-sections, table headers |
| Body | 14px | 400 | Primary content, descriptions |
| Body Small | 13px | 400 | Secondary content, metadata |
| Label / UI | 12px | 500 | Navigation, badges, axis labels |
| Caption | 11px | 400 | Timestamps, footnotes |

Note: Sizes are intentionally smaller than Conversational — density is a feature, not a compromise.

```tsx
// Font setup in layout.tsx
import { DM_Sans } from 'next/font/google'
const dmSans = DM_Sans({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-dm-sans',
})
```

---

## Colors

Warm stone neutrals with amber as the primary accent. Feels considered and grounded — not cold, not corporate.

Always use semantic tokens. Never use raw hex values in components.

| Token | Value | Usage |
|---|---|---|
| `bg-background` | #F5F3F0 | App background — warm off-white |
| `text-foreground` | #1C1917 | Primary text — warm near-black |
| `bg-primary` | #92400E | Primary actions — warm amber-brown |
| `text-primary-foreground` | #FEF3C7 | Text on primary surfaces |
| `bg-secondary` | #E7E3DD | Secondary surfaces |
| `bg-muted` | #EEEBE6 | Muted backgrounds, row stripes |
| `text-muted-foreground` | #78716C | Secondary text, metadata |
| `bg-accent` | #FEF3C7 | Amber wash, highlights |
| `accent-foreground` | #1C1917 | Text on accent surfaces |
| `border-border` | #DDD9D3 | Dividers, card outlines |
| `ring-ring` | #D97706 | Focus rings — amber |
| `text-destructive` | #DC2626 | Errors, critical states |

### Data visualisation
| Token | Value | Usage |
|---|---|---|
| `--chart-1` | #D97706 | Amber — primary series |
| `--chart-2` | #0F766E | Teal — secondary series |
| `--chart-3` | #7C3AED | Violet — tertiary series |
| `--chart-4` | #DC2626 | Red — alert series |
| `--chart-5` | #78716C | Stone — neutral series |

---

## Components

### Buttons
```tsx
// Primary
<Button className="h-8 text-xs px-3">Run Report</Button>

// Secondary
<Button variant="outline" className="h-8 text-xs px-3">Export</Button>

// Ghost — table actions, inline controls
<Button variant="ghost" className="h-7 text-xs px-2">Edit</Button>
```
Smaller than default — `h-8` standard, `h-7` compact. Radius: `6px`. Weight: 500.

### Cards
```tsx
<Card className="rounded-lg border border-border shadow-none p-4 bg-card">
  <h3 className="text-sm font-semibold text-foreground">Metric Title</h3>
  <p className="text-xs text-muted-foreground mt-0.5">Subtitle</p>
</Card>
```
No shadow — borders define surfaces. Tighter padding than other themes.

### Badges
```tsx
<Badge variant="outline" className="text-[11px] font-medium rounded-md px-1.5">
  Active
</Badge>
```
Slightly squared — `rounded-md` not pill. Compact and informational.

### Inputs
```tsx
<Input placeholder="Filter..." className="h-8 rounded-md text-sm" />
```
Height: `32px` · Radius: `rounded-md` · Compact, efficient

### Tables
Tables are first-class citizens in this theme.
```tsx
<Table>
  <TableHeader>
    <TableRow className="bg-muted">
      <TableHead className="text-xs font-medium text-muted-foreground h-8">Column</TableHead>
    </TableRow>
  </TableHeader>
  <TableBody>
    <TableRow className="hover:bg-muted/50 border-b border-border">
      <TableCell className="text-sm py-2">Value</TableCell>
    </TableRow>
  </TableBody>
</Table>
```
Row height: `40px` default, `32px` compact. Subtle stripe with `bg-muted` on header.

### Page layout
```tsx
<div className="max-w-7xl mx-auto px-4 py-6">
  {/* wider max-width, tighter padding than other themes */}
</div>
```

---

## Spacing

Tighter than Conversational and Vital — density is intentional.

| Value | Usage |
|---|---|
| 4px | Icon gap, tight inline, table cell padding |
| 8px | Tag padding, compact card gap |
| 12px | Card padding (compact), list items |
| 16px | Card padding (default), section gap |
| 24px | Between components |
| 32px | Section vertical rhythm |
| 48px | Major page sections |

---

## Border Radius

Intentionally more restrained than the other themes — precision over softness.

| Value | Usage |
|---|---|
| 4px | Badges, tight elements |
| 6px | Buttons |
| 8px | Inputs, cards (compact) |
| 12px | Cards (default), modals |
| Full | Only for avatars, status dots |

---

## Data visualisation rules

- Minimal grid lines — use `stroke-dasharray` subtle dashes only
- Precise axis labels at `11px` caption size
- Use `--chart-*` tokens only — never custom colors per chart
- No decorative chart elements — no gradients, no shadows on bars
- Always include a legend when more than one series

---

## Don'ts

- Never introduce a second typeface
- Never use raw hex values in components
- Never use pill-shaped badges — this theme is precise not playful
- Never use large padding or generous whitespace where compact works
- Never use arbitrary Tailwind spacing values
- Never use filled icons
- Never add decorative elements to charts
- Never use `ease-in-out` or `linear` transitions
- Never use raw `<button>` or `<input>` elements
