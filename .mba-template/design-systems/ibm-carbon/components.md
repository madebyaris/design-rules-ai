# IBM Carbon — Components Cheat Sheet

**Canonical docs:** https://carbondesignsystem.com

**What to copy from this system:** enterprise data-density, IBM Plex typography, rigorous WCAG 2.1 AA compliance, deep component coverage for B2B.

---

## When to choose Carbon

- Enterprise SaaS, B2B dashboards, data-heavy admin tools.
- Highly regulated industries (finance, healthcare, gov).
- Apps requiring extensive form patterns (filters, multi-step wizards, complex tables).
- Teams that value comprehensive React/Web Component libraries with long-term support.

---

## Defining traits

| Trait | How |
|-------|-----|
| **2x grid** | All measurements are multiples of 2px. Spacing scale: 2, 4, 8, 12, 16, 24, 32, 40, 48, 64, 80, 96, 160. |
| **IBM Plex Sans / Mono** | Designed in-house for clarity at small sizes. Distinctive but neutral. |
| **High data density** | Default sizes are dense (sm = 32px). `xl` = 48px is the largest. |
| **Strong a11y** | WCAG 2.1 AA baseline. Focus indicators are 2px solid. |
| **Comprehensive theming** | White, Gray 10, Gray 90, Gray 100 themes. Switchable. |
| **Productive vs Expressive** | Productive = data-dense (default). Expressive = marketing-leaning, more whitespace. |

---

## Component patterns

| Component | Notable detail |
|-----------|---------------|
| **Data Table** | Sortable, expandable, batch-actions, sticky header, dense/compact/normal/tall sizes. |
| **Multi-Select** | Token-based with combobox filtering. |
| **Date Picker** | Range picker, calendar grid, locale-aware. |
| **File Uploader** | Drag-drop + button, multi-file, status per file. |
| **Tile** | Clickable / Selectable / Expandable variants. Used heavily as alt to cards. |
| **Notification** | Inline (in-flow), Toast (transient), Actionable (with button). |
| **Accordion** | Single or multi-expand, with chevron animations. |
| **Loading** | Inline (button-sized), Section, Page, Overlay. |
| **Number Input** | Spinner buttons, keyboard arrow up/down, min/max validation. |

---

## Color tokens

```
$background, $background-hover, $background-active, $background-selected
$layer-01, $layer-02, $layer-03  (3 levels of surface elevation)
$text-primary, $text-secondary, $text-placeholder, $text-helper, $text-on-color
$border-subtle, $border-strong, $border-inverse
$support-error, $support-success, $support-warning, $support-info
```

Tokens are theme-aware — same name, different value across White/Gray themes.

---

## Implementation

- React: `@carbon/react` (v1 and beyond).
- Web Components: `@carbon/web-components`.
- Vue, Angular, Svelte: official ports exist.

---

## What to AVOID copying

- Don't use Carbon for consumer products — it reads as "enterprise IBM software", which can feel sterile.
- Don't ignore the productive/expressive distinction — using productive density for marketing pages feels cramped.
- Don't override IBM Plex without a specific brand reason — it's tuned for the system.
- Don't mix Carbon with Material — they share grid concepts but diverge in motion, color, and density.
