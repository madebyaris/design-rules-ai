# Container Queries

Container queries let a component respond to its **own** size, not the viewport. This is the modern default for responsive components inside grids, sidebars, and unknown contexts.

Browser support: Chrome 105+, Safari 16+, Firefox 110+ (effectively universal in 2026).

---

## When to use

- Use **container queries** for: cards in a grid, sidebar widgets, embedded components, anything that might appear at different sizes.
- Use **media queries** for: page layout, navigation chrome, sidebar show/hide, font scaling.

A media query asks "how wide is the screen?" A container query asks "how wide is this component?". The latter composes; the former doesn't.

---

## Setup

Mark a parent as a containment context:

```css
.card-grid {
  container-type: inline-size;
  container-name: card;  /* optional but readable */
}
```

`inline-size` queries width only (most common). `size` queries both dimensions but disables children's auto-height (rarely what you want).

---

## Query

```css
.card { padding: var(--space-3); }

@container card (min-width: 480px) {
  .card { padding: var(--space-6); }
}

@container card (min-width: 640px) {
  .card {
    display: grid;
    grid-template-columns: 120px 1fr;
    gap: var(--space-4);
  }
}
```

Now the card lays out based on its slot, not the viewport. Drop it in a sidebar (narrow), it stays compact. Drop it in a full-width row, it expands.

---

## Container query units

These units resolve relative to the nearest container, not the viewport:

| Unit | Meaning |
|------|---------|
| `cqw` | 1% of container width |
| `cqh` | 1% of container height |
| `cqi` | 1% of container inline size |
| `cqb` | 1% of container block size |
| `cqmin` | smaller of `cqi` / `cqb` |
| `cqmax` | larger of `cqi` / `cqb` |

Example — typography that scales with the card, not the screen:

```css
.card-title { font-size: clamp(1rem, 4cqi, 1.5rem); }
```

---

## Composition pattern

A reusable component should set its own container if it owns its layout:

```css
.product-card {
  container-type: inline-size;
}

.product-card__layout {
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
}

@container (min-width: 400px) {
  .product-card__layout {
    flex-direction: row;
    align-items: center;
  }
}
```

Note: when omitting `container-name`, queries match the nearest containing container ancestor.

---

## Style queries (newer, Chrome 111+)

Query parent's custom property — useful for theme-aware components:

```css
@container style(--theme: dense) {
  .card { padding: var(--space-2); }
}
```

Set the theme on a wrapper: `<div style="--theme: dense; container-type: inline-size">...</div>`.

Use sparingly — it's still niche and harder to debug than class-based variants.

---

## Common pitfalls

- **`overflow: visible` is forbidden** on `container-type: size` containers. Use `inline-size` if you need overflow visibility (which is most of the time).
- Containers create a new containing block — `position: fixed` children won't escape.
- Don't put container queries in `:root` or `html` (the document is already viewport-relative — use a media query).
- Container queries don't apply to the container itself, only its descendants. To restyle the container, query its own parent or use `:has()`.

---

## When NOT to use

- Page-level layout (use media queries).
- Showing/hiding nav patterns (tied to viewport, use media queries).
- Print styles (use `@media print`).
