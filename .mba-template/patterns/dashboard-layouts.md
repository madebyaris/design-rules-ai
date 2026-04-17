# Dashboard Layouts — Anatomy

Density: **compact**. Scan: **F-pattern**. One primary action in the page header.

---

## Shell archetypes

Pick one. Don't mix.

### A. Sidebar + main (default for SaaS)

```
┌────────────────────────────────────────────┐
│ Header (56–64px, sticky)                   │
├────────┬───────────────────────────────────┤
│        │ Page header (title + actions)     │
│ Sidebar│ ─────────────────────────────────│
│ 240px  │ Filters / search                  │
│        │ ─────────────────────────────────│
│        │ Metrics row (KPI cards)           │
│        │ ─────────────────────────────────│
│        │ Primary view (table / chart)      │
│        │                                   │
└────────┴───────────────────────────────────┘
```

When to use: app with persistent navigation across many sections. Standard for SaaS tools, admin panels.

### B. Top nav + main (for fewer sections)

When to use: marketing-leaning dashboards (analytics readouts), apps with ≤5 main sections. Header carries nav, no sidebar.

### C. Three-pane (mail / chat / IDE pattern)

```
┌─────┬──────────┬──────────────────────────┐
│ Nav │ List     │ Detail                   │
│ 56  │ 280–320  │ flex                     │
└─────┴──────────┴──────────────────────────┘
```

When to use: list-detail apps (email, messaging, CRM, file browsers).

---

## Header (56–64px, sticky)

Contents (left-to-right):
- **Brand** (24–32px logo, optional).
- **Search** (center or left, 320–480px wide). `<input type="search">` with leading icon.
- **Notifications** (icon button, badge for unread count).
- **Help / docs** (icon button, optional).
- **Profile menu** (avatar 32px + dropdown).

Don't put filters or page-specific actions in the header. Those live in the page header below.

---

## Sidebar (240–280px, collapsible to 56–64px)

- **Brand** (top, repeats from header on collapse).
- **Primary nav** (sections grouped, with section labels in 11px uppercase muted).
- Each item: icon (20px) + label (14px). Active state: left border 3px in `--color-accent` OR background tint, never both.
- **Secondary nav at bottom**: settings, help, profile.
- **Collapse toggle** at bottom-left.

Keyboard: `[` and `]` to toggle in apps that lean keyboard-first (Linear-style).

---

## Page header

```
H1: Dashboard name           [Filter] [Date▾] [+ New invoice (primary)]
Breadcrumbs (optional, muted)
```

- Left: H1 (24–32px) + optional breadcrumbs above (12px muted).
- Right: filter chips, date range picker, and **one** primary action button.
- Below: tabs OR filter row (chips).

**Rule:** ONE primary action. The "+ New" / "Create" / "Export" button. Everything else (filter, search, settings) is secondary.

---

## Metrics row (KPI cards)

- Grid: 2–4 cards. `grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))`.
- Each card:
  - Label (12–14px, muted, uppercase optional).
  - Value (24–32px, semibold or 600, tabular numerals: `font-variant-numeric: tabular-nums`).
  - Change vs previous period (12–14px, success/danger color + arrow icon).
  - Optional sparkline (60×24px, accent color, no axis).
- Use realistic numbers from `content/sample-content.json`: `$1,234,567` not `$1,000,000`. `+12.4%` not `+10%`.

---

## Primary view options

Pick one as the main view per page:

### Data table

- Columns: 4–8. Sticky header. Sortable (icon in `<th>`, `aria-sort`).
- Row height: 32px (compact density).
- Right-align numbers. Tabular numerals.
- Row hover: `--color-bg-muted` bg.
- Row actions: ellipsis menu (right-aligned cell) OR action icons revealed on hover.
- Empty: icon + message + create CTA.
- Loading: 5–10 skeleton rows.
- Error: inline alert + retry button.
- Pagination: bottom-right (page size selector + page nav).

### Chart

- Library: Recharts, Visx, ECharts, Chart.js — pick what's already in your stack.
- Title (H3) + time range selector (top right).
- Y-axis with units, X-axis with tick labels (don't crowd — show every Nth).
- Tooltip on hover with full precision.
- Legend if >1 series, omitted if 1.
- Mobile: full width, swipe to pan if zoomed.

### Kanban / board

- Columns scroll horizontally on overflow.
- Each column: header (label + count), card stack, "+ Add" at bottom.
- Cards: drag-and-drop, keyboard accessible (`role="listbox"` etc.).

---

## Secondary view (right column or below)

Common patterns:
- **Activity feed** — avatar + action + timestamp (relative: "2h ago").
- **Recent items** — small list with icons.
- **Tips / onboarding** — dismissible card with checklist.
- **Status widgets** — system health, recent errors.

---

## Filter / search row

- Search input (icon left, clear icon right when populated).
- Filter chips: removable tags with x icon. Show only active filters.
- "More filters" button → opens modal/sheet for advanced filtering.
- Sort dropdown (right-aligned).
- Clear all (text link, right).

---

## Empty / loading / error states (required for every data block)

- **Empty:** icon (48–64px, muted) + heading + 1–2 sentence description + primary CTA. Specific to context: "No invoices yet. Create your first invoice." Not "No data".
- **Loading:** skeleton (preferred) or centered spinner. Skeleton matches final layout.
- **Error:** alert with message + retry button. Don't show stack traces. Log them.

---

## Responsive behavior

| Breakpoint | Behavior |
|------------|----------|
| < 640px (mobile) | Sidebar hidden behind hamburger. Metrics 1-col. Tables → card list. |
| 640–1024px (tablet) | Sidebar collapsed (icons). Metrics 2-col. Tables horizontally scroll. |
| ≥ 1024px (desktop) | Full sidebar. Metrics 3–4 col. Full table width. |

---

## Density

Dashboards are compact by default:
- Body text 13–14px.
- Row height 32px.
- Padding `--space-2` to `--space-3` inside controls.
- Card padding `--space-4`.

Use `comfortable` only for analytics dashboards aimed at executives, where density matters less than clarity.

---

## Sample dashboard archetypes

| Type | Metrics | Primary view | Secondary |
|------|---------|--------------|-----------|
| Sales | Revenue, Orders, Conversion, AOV | Revenue chart over time | Recent orders table |
| Analytics | Users, Sessions, Bounce, Avg duration | Traffic chart | Top pages table |
| Admin | Total users, Active sessions, Storage | User table | System logs |
| Monitoring | Uptime, Response time, Error rate | Performance chart | Recent incidents |
| Content CMS | Posts published, Drafts, Views | Posts table | Recent activity |
| Finance | Balance, MRR, Burn, Runway | MRR chart | Recent transactions |
