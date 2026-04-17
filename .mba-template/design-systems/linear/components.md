# Linear — Components Cheat Sheet

**Canonical docs:** https://linear.app (no public design system docs — observe the product).

**What to copy from this system:** keyboard-first interactions, command palette, instant feel, ruthless density without clutter.

Linear is the gold standard for "doesn't look AI-generated" because every detail is deliberate.

---

## When to choose Linear-style

- Productivity apps, project management, issue trackers.
- Power users who'll learn keyboard shortcuts.
- You want instant perceived performance.
- Apps with high content density (lists, tables, hierarchies).

---

## Defining traits

| Trait | How |
|-------|-----|
| **Keyboard-first** | Every action has a shortcut. `?` opens the cheat sheet. `Cmd+K` opens command palette. |
| **Command palette (Cmd+K)** | Single search-anywhere UI: navigate, create, search, run actions. |
| **Instant transitions** | View transitions <150ms. Optimistic UI everywhere. |
| **Compact density** | 28–32px row height, 13px body, lots of info per screen. |
| **Subtle dark theme** | Default dark, near-black bg with very low chroma neutrals. |
| **Status as primary signal** | Issue status (Triage / Backlog / Started / Done) drives the visual hierarchy with colored dot icons. |
| **Inline actions** | Hover a row → reveal actions. No menu trips for common tasks. |

---

## Component patterns

| Component | Notable detail |
|-----------|----------------|
| **Sidebar** | Workspaces top, projects nested, "Views" section. Keyboard `[/]` to collapse. |
| **List view** | Sortable, group-by, swipe-to-reveal actions. Each row has a status dot icon. |
| **Issue row** | Status icon + ID + title + assignee + priority + date, all inline, fixed-width columns for scannability. |
| **Issue detail** | Two-column: properties sidebar (right) + body (left). Inline editable everything. |
| **Command palette** | Fuzzy search, recent items, keyboard nav, custom commands per context. |
| **Keyboard hints** | Letters appear next to menu items on hover (`G then I` = Go to Inbox). |
| **Toast** | Minimal, top-center, fades in 200ms, dismisses 3s. |
| **Avatar** | Initials with deterministic color, never generic icon. |

---

## Color & contrast

- **Dark mode default.** Light mode is secondary.
- Background: `oklch(0.165 0.005 250)` — slight blue undertone, not pure gray.
- Text: `oklch(0.92 0.01 250)` — soft white, not pure.
- Accent (purple): `oklch(0.65 0.18 290)`.
- Status colors are saturated but small (8px dot icons), never large fills.

---

## Motion

- View transitions: 150–200ms ease-out.
- Hover: 80ms ease-out (faster than default, feels instant).
- Page transitions: instant (no fade) — relies on persistent shell.
- Easing: `cubic-bezier(0.2, 0, 0, 1)` (Linear's signature).

---

## Typography

```css
font-family: "Inter Variable", "Inter", system-ui, sans-serif;
font-feature-settings: "cv11", "ss01", "ss03";
font-variant-numeric: tabular-nums;
```

Tight letter-spacing on small text (-0.01em). Consistent 13px body, 14px UI labels.

---

## What to AVOID copying

- Don't add Linear-style commands without actually wiring keyboard shortcuts — the visual cue without the function is fake.
- Don't go full near-black bg without testing contrast (4.5:1 is hard at low chroma).
- Don't copy the cmd palette UI without the search/action backend — it's worse than no palette.
- Don't try to be Linear if your audience isn't power users (they'll feel overwhelmed).
