---
name: mba-build-component
description: Generate a production-ready, accessible component using MBA design rules
---

# MBA Build Component

Generate a single, production-ready component. This command is a **thin orchestrator** — the design rules live in `.cursor/rules/`, not here.

## Arguments

- `component_name` (required) — e.g. `button`, `input`, `card`, `data-table`, `combobox`.
- `framework` (optional, default `html`) — `html` | `react` | `vue` | `svelte` | `web-component` | `react-native`.
- `variants` (optional) — comma-separated. Default depends on component (e.g. button → `primary,secondary,ghost,danger`).
- `sizes` (optional) — comma-separated. Default `sm,md,lg`.
- `density` (optional, default `comfortable`) — `compact` | `comfortable` | `spacious`.
- `system` (optional, default `shadcn-ui`) — design system to emulate: `shadcn-ui` | `vercel-geist` | `linear` | `material-design-3` | `apple-hig` | `adobe-spectrum` | `ibm-carbon` | `microsoft-fluent-2`.
- `with_examples` (optional, default `true`) — generate a usage example file.

## Procedure

Run these steps in order. Do not skip the self-critique.

### 1. READ the rules (in order)

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — principles + non-negotiables + self-critique.
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — every approved value. Use ONLY these.
- `[.cursor/rules/50-components.mdc](mdc:.cursor/rules/50-components.mdc)` — anatomy framework + 8-state matrix.

### 2. READ the reference

- `[.mba-template/design-systems/{system}/components.md](mdc:.mba-template/design-systems/)` — what to copy from the chosen design system.
- Matching example HTML in `[.mba-template/examples/](mdc:.mba-template/examples/)` if it exists (button, input, card, modal, table, nav, empty-state, skeleton).
- `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)` — token variable names.

### 3. PLAN (write 5 lines before writing code)

Answer in your own words:

1. Container, content, affordances, states, density (the 5-part anatomy).
2. Which of the 8 states apply (default, hover, focus-visible, active, disabled, loading, empty, error)?
3. Density commitment (compact / comfortable / spacious) and which token vars that maps to.
4. Reference design system (`{system}`) — what specifically you're borrowing.
5. Accessibility notes (semantic element, ARIA needs, keyboard model).

### 4. GENERATE

Output the component using the framework selected. Reference design tokens via CSS variables — never hardcode pixel values, hex codes, or font sizes.

#### HTML / CSS shape

```html
<button class="btn btn--primary btn--md" type="button">
  <i class="fa-solid fa-save" aria-hidden="true"></i>
  <span>Save changes</span>
</button>
```

```css
.btn {
  height: var(--component-row-h, 40px);
  padding: 0 var(--space-4);
  font: inherit;
  font-size: var(--font-size-sm);
  font-weight: 500;
  border: 1px solid transparent;
  border-radius: var(--radius-sm);
  cursor: pointer;
  transition: background var(--duration-fast) var(--easing-out),
              transform var(--duration-fast) var(--easing-out);
  /* ...all 8 states defined below... */
}
```

#### React shape (TS)

```tsx
import { cva, type VariantProps } from "class-variance-authority";

const button = cva("btn", {
  variants: {
    variant: { primary: "btn--primary", secondary: "btn--secondary", ghost: "btn--ghost", danger: "btn--danger" },
    size: { sm: "btn--sm", md: "btn--md", lg: "btn--lg" },
  },
  defaultVariants: { variant: "primary", size: "md" },
});

interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement>, VariantProps<typeof button> {
  loading?: boolean;
}

export function Button({ variant, size, loading, children, className, ...rest }: ButtonProps) {
  return (
    <button className={button({ variant, size, className })} disabled={loading || rest.disabled} {...rest}>
      {loading ? <Spinner /> : children}
    </button>
  );
}
```

### 5. SELF-CRITIQUE (Layer C from `00-design-principles.mdc`)

Score 1–5 on each. If any < 4, revise once before returning.

- **Hierarchy** — is the primary visual emphasis on the most important element?
- **Restraint** — anything you could remove and lose nothing?
- **Rhythm** — every value from `10-tokens-and-scales.mdc`?
- **Content fit** — realistic example copy (no Lorem, no "Acme")?
- **Accessibility** — semantic HTML, focus-visible distinct from hover, ARIA, 44px touch targets?
- **Reference** — would this look at home in the chosen design system's codebase?

Then run the **anatomy + states checklist** from `50-components.mdc` §8.

### 6. OUTPUT

Files to create (exact paths):

| Framework | Files |
|-----------|-------|
| `html` | `components/{name}.html`, `components/{name}.css` |
| `react` | `components/{Name}.tsx`, `components/{name}.module.css` (or Tailwind classes inline) |
| `vue` | `components/{Name}.vue` |
| `svelte` | `components/{Name}.svelte` |
| `web-component` | `components/{name}-element.ts` |

If `with_examples=true`: also create `examples/{name}-example.{ext}` showing all variants × all sizes × key states.

Finish with a 1-paragraph rationale: which design system you emulated and why, and the one most-important design decision.

## Common components — quick reference

| Component | Default variants | Default sizes | Notable states beyond the 8 |
|-----------|-----------------|---------------|------------------------------|
| `button` | primary, secondary, ghost, danger, link | sm 32 / md 40 / lg 48 | — |
| `input` | text, email, password, search, number | sm 32 / md 40 / lg 48 | readonly |
| `card` | flat, elevated, interactive | — | — |
| `modal` | sm 400 / md 600 / lg 800 / full | — | open, closing |
| `data-table` | basic, selectable, sortable | compact / comfortable / spacious rows | sorted-asc, sorted-desc |
| `dropdown` | menu, select, combobox | — | open |
| `toast` | success, warning, danger, info | — | entering, exiting |
| `tabs` | underline, filled, pills | — | — |

## Example invocations

```
/mba-build-component component_name="button" framework="react" variants="primary,secondary,ghost,danger"
/mba-build-component component_name="data-table" framework="react" density="compact" system="vercel-geist"
/mba-build-component component_name="modal" framework="html" sizes="sm,md,lg"
```

## Definition of done

- [ ] All 8 states defined or N/A documented.
- [ ] `:focus-visible` ring distinct from `:hover`.
- [ ] Semantic element used (button, dialog, table, nav).
- [ ] All values from `10-tokens-and-scales.mdc` (no hardcoded px / hex).
- [ ] Empty / loading / error states for any data-dependent component.
- [ ] No generated SVG — icons from a library.
- [ ] Example file shows all variants × all sizes.
- [ ] 1-paragraph design rationale written.
