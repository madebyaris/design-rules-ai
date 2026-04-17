---
name: mba-build-dashboard-page
description: Generate a compact-density, data-rich dashboard page using MBA design rules
---

# MBA Build Dashboard Page

Generate a complete dashboard page. Density is **compact** by default — dashboards are for power users.

## Arguments

- `dashboard_type` (required) — `sales` | `analytics` | `admin` | `monitoring` | `cms` | `finance` | `custom`.
- `metrics` (optional) — comma-separated KPIs. Default depends on `dashboard_type` (see below).
- `primary_view` (optional, default `table`) — `table` | `chart` | `kanban` | `mixed`.
- `shell` (optional, default `sidebar-main`) — `sidebar-main` | `top-nav-main` | `three-pane`.
- `system` (optional, default `linear`) — design system to emulate (linear, vercel-geist, ibm-carbon recommended).
- `density` (optional, default `compact`) — `compact` | `comfortable`. **Spacious not allowed for dashboards.**
- `framework` (optional, default `html`) — `html` | `react` | `vue` | `svelte`.

## Procedure

### 1. READ the rules

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — restraint, hierarchy, content-fits-layout.
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — compact density spec (§10).
- `[.cursor/rules/50-components.mdc](mdc:.cursor/rules/50-components.mdc)` — required 8 states for every interactive piece.
- `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` — dashboard archetype.

### 2. READ the references

- `[.mba-template/patterns/dashboard-layouts.md](mdc:.mba-template/patterns/dashboard-layouts.md)` — shell options, header, sidebar, KPI row, primary view variants.
- `[.mba-template/design-systems/{system}/components.md](mdc:.mba-template/design-systems/)` — component look + feel.
- `[.mba-template/content/sample-content.json](mdc:.mba-template/content/sample-content.json)` — realistic data. **Use these.** Never `User 1`, `$1,000.00`, "+10%".
- `[.mba-template/examples/table.html](mdc:.mba-template/examples/table.html)`, `[nav.html](mdc:.mba-template/examples/nav.html)`, `[empty-state.html](mdc:.mba-template/examples/empty-state.html)`, `[skeleton.html](mdc:.mba-template/examples/skeleton.html)` — patterns to mirror.

### 3. PLAN

Write these out before generating:

1. **Shell archetype** (sidebar-main / top-nav-main / three-pane) and why.
2. **Header** contents — brand, search, notifications, profile.
3. **Sidebar** sections — group by workspace, account, etc.
4. **Page header** — H1 + breadcrumbs + filters + the ONE primary action.
5. **KPI row** — 2–4 metrics with realistic values (use `sample-content.json`):
   - Label / value / change vs previous period / optional sparkline.
6. **Primary view** — table, chart, or kanban — fully designed (columns, sortable, hover, empty/loading/error).
7. **Secondary view** (optional) — activity feed, recent items, status widgets.
8. **Density** — confirm compact (32px row, 13–14px body, `--space-2`/`--space-3` padding).

### 4. STATES MATRIX (required for every data block)

| Block | Empty | Loading | Error | Default |
|-------|-------|---------|-------|---------|
| KPI cards | "—" placeholder | Skeleton number bar | "Couldn't load" with retry | Real number |
| Table | Empty state w/ icon + CTA | Skeleton rows | Inline alert + retry | Rows |
| Chart | "No data for this range" | Skeleton chart | Inline alert + retry | Chart |
| Sidebar items | n/a | n/a | n/a | n/a |

Generate all four states for the table and at least the empty + loading for KPIs.

### 5. GENERATE

- Use semantic landmarks: `<header>`, `<aside>`, `<nav>`, `<main>`.
- Wrap the page root in `<div class="page-compact">` (or comfortable) so `--component-padding` and `--component-row-h` resolve.
- Use `font-variant-numeric: tabular-nums` on every numeric cell.
- Right-align numeric columns.
- Sticky table header.
- Hover bg `--color-bg-muted` on rows.
- Active nav item gets a left accent bar OR bg tint, never both.

### 6. SELF-CRITIQUE (Layer C)

Score 1–5 on each. If any < 4, revise once.

- **Hierarchy** — one primary action per page header? Active nav obvious?
- **Restraint** — no redundant chrome, no decoration in tables, no unnecessary section?
- **Rhythm** — every spacing/radius/font value from `10-tokens-and-scales.mdc`?
- **Density** — compact density honored? No mixed densities (e.g. comfortable cards inside a compact table)?
- **Realism** — numbers, names, dates, IDs all believable (no `User 1`, no `$1,000.00`)?
- **States** — empty / loading / error rendered for every data-dependent block?
- **Reference** — at home in Linear / Geist / Carbon?

### 7. OUTPUT

| Framework | Files |
|-----------|-------|
| `html` | `pages/dashboard.html`, `styles/dashboard.css` |
| `react` | `app/dashboard/page.tsx` (Next.js) or `src/pages/Dashboard.tsx` |
| `vue` | `src/views/Dashboard.vue` |
| `svelte` | `src/routes/dashboard/+page.svelte` |

End with a 1-paragraph rationale: design system emulated, the density choice, and the most-used real-world dashboard you're modeling after (e.g. "Linear's project view", "Stripe's revenue dashboard").

## Default metrics by dashboard type

| Type | Suggested KPIs |
|------|----------------|
| sales | Revenue · Orders · Conversion rate · Avg order value |
| analytics | Users · Sessions · Bounce rate · Avg duration |
| admin | Total users · Active sessions · Storage used · API calls |
| monitoring | Uptime % · Avg response time · Error rate · Incidents |
| cms | Posts published · Drafts · Views · Comments |
| finance | Balance · MRR · Burn rate · Runway |

## Example invocations

```
/mba-build-dashboard-page dashboard_type="sales" framework="react" system="vercel-geist"
/mba-build-dashboard-page dashboard_type="monitoring" primary_view="chart" shell="sidebar-main" system="linear"
/mba-build-dashboard-page dashboard_type="custom" metrics="MRR,Active workspaces,Trial conversions,NPS" primary_view="mixed"
```

## Definition of done

- [ ] Density: compact (or comfortable if argued).
- [ ] One primary action in the page header.
- [ ] Realistic numbers + names from `sample-content.json`.
- [ ] Tabular numerals on numeric columns, right-aligned.
- [ ] Empty / loading / error states for the table and the KPI row.
- [ ] Active nav state distinct (one signal, not two).
- [ ] Sidebar collapses to icons or hamburger on narrow viewports.
- [ ] Mobile: tables horizontally scroll OR collapse to card list.
- [ ] No mixed densities on the page.
- [ ] 1-paragraph rationale written.
