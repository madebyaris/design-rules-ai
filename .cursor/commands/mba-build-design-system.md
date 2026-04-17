---
name: mba-build-design-system
description: Scaffold a complete design system (tokens + primitives + components) using MBA design rules
---

# MBA Build Design System

Scaffold a project's design system from scratch: tokens, primitives, base components, and a documentation page. Default to the **modern token layer** (OKLCH, `light-dark()`, fluid type) — falls back to legacy on `--legacy`.

## Arguments

- `system_name` (required) — e.g. `lumina-ui`, `helm-design`.
- `accent_hue` (optional, default `260`) — OKLCH hue (0–360). Try: blue 250, indigo 260, purple 290, green 145, red 25.
- `base_system` (optional, default `shadcn-ui`) — system to base off: `shadcn-ui` | `vercel-geist` | `linear` | `material-design-3` | `apple-hig` | `adobe-spectrum` | `ibm-carbon` | `microsoft-fluent-2`.
- `framework` (optional, default `react`) — `react` | `vue` | `svelte` | `web-components` | `vanilla`.
- `css_approach` (optional, default `tailwind-v4`) — `tailwind-v4` | `vanilla-css` | `css-modules` | `styled-components`.
- `legacy` (optional flag) — use 2025 `tokens.css` instead of `tokens-modern.css`.

## Procedure

### 1. READ the rules

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — taste + non-negotiables.
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — every approved scale.
- `[.cursor/rules/50-components.mdc](mdc:.cursor/rules/50-components.mdc)` — anatomy + states matrix per component.

### 2. READ the references

- `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)` — copy as starting point (preferred).
- `[.mba-template/tokens/tokens.css](mdc:.mba-template/tokens/tokens.css)` — legacy fallback (`--legacy` flag).
- `[.mba-template/design-systems/{base_system}/components.md](mdc:.mba-template/design-systems/)` — what to copy from this base.
- `[.mba-template/patterns/dark-mode.md](mdc:.mba-template/patterns/dark-mode.md)` — theme pattern.
- `[.mba-template/examples/](mdc:.mba-template/examples/)` — existing primitives to mirror.

### 3. PLAN

Write out:

1. **Token plan** — accent hue, neutral scale (true gray vs slight tint), typography stack, base radius (sm 4 / md 6 / md 8), motion easing personality (calm Geist vs expressive Material).
2. **Primitive list** — exact components to ship in v0.1 (typically 8–12): Button, Input, Textarea, Select, Checkbox, Radio, Card, Modal, Toast, Avatar, Badge, Spinner.
3. **Theme plan** — light only, light + dark via `light-dark()` (recommended), or three-state (system/light/dark).
4. **Distribution model** — paste-into-app (shadcn style) OR npm package OR monorepo workspace.

### 4. GENERATE structure

Output a registry-style folder layout (modeled on shadcn/ui):

```
{system_name}/
├── README.md                      # what it is, how to use, contribution
├── tokens/
│   ├── tokens.css                 # copy/adapt from tokens-modern.css
│   └── theme.config.{ts|json}     # token values exported for Tailwind/JS
├── primitives/                    # framework-specific UI components
│   ├── Button.{tsx|vue|svelte}
│   ├── Input.{tsx|vue|svelte}
│   ├── Card.{tsx|vue|svelte}
│   ├── Modal.{tsx|vue|svelte}
│   └── ...
├── styles/
│   ├── reset.css                  # modern reset (Andy Bell + tweaks)
│   ├── globals.css                # body defaults, focus-visible, density classes
│   └── utilities.css              # layout primitives (Stack, Cluster, Grid, Sidebar, Switcher, Cover)
├── patterns/                      # composed patterns (see .mba-template/patterns/)
│   ├── dark-mode.md
│   └── view-transitions.md
└── docs/
    ├── index.html                 # showcase page (each primitive in all variants × states)
    └── tokens.html                # token reference page
```

### 5. TOKENS — modern (default)

Generate `tokens/tokens.css` based on `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)`, with:

- `--accent-500: oklch(0.62 0.188 {accent_hue})` and the rest of the accent ramp interpolated.
- `light-dark(...)` semantic tokens.
- Fluid type via `clamp()`.
- Z-index scale (9 tokens), shadow scale (5 tokens), elevation system.
- `@property` declarations for animatable custom properties.
- `view-transition-name` reservations.

If `--legacy`: copy `tokens.css` verbatim (no OKLCH, no `light-dark()`, no fluid type) and skip the modern features above.

### 6. CSS approach branches

- **`tailwind-v4`** — emit a `tailwind.config.{ts|js}` ONLY for plugins. Use `@theme` block in CSS for tokens (Tailwind v4 reads CSS vars directly). Components use Tailwind utility classes derived from tokens.
- **`vanilla-css`** — `tokens.css` + per-component `.css` files. Components use BEM or utility-first hand-rolled.
- **`css-modules`** — `Component.module.css` per component.
- **`styled-components`** — emit a `theme.ts` exporting tokens, wrap with `<ThemeProvider>`, use `${({theme})=>theme.color.fg}` references.

### 7. PRIMITIVES — minimum 8

For each primitive, follow `[.cursor/rules/50-components.mdc](mdc:.cursor/rules/50-components.mdc)` — all 8 states. Write each as a thin orchestrator → reference the corresponding `.mba-template/examples/{name}.html` for the styling pattern.

### 8. SELF-CRITIQUE (Layer C)

Score 1–5 on each. Revise if any < 4.

- **Coherence** — every primitive looks like it belongs to the same system?
- **Restraint** — could any token, variant, or primitive be removed without loss?
- **Token compliance** — every primitive uses only tokens (no inline px / hex)?
- **States completeness** — every primitive has all 8 states or N/A documented?
- **Theme** — light + dark both designed (not just inverted)?
- **A11y baseline** — semantic HTML, focus-visible distinct, ARIA where needed?
- **Reference fidelity** — primitives feel like the chosen `base_system`?

### 9. OUTPUT

Files exactly as in step 4. Write a README with:

- One-paragraph philosophy.
- Token quick reference (link to `tokens.css`).
- Component checklist (✅ ones included in v0.1, ⏳ planned).
- Install snippet.
- Example usage of Button + Input + Card.
- Link to docs page.

End with a 1-paragraph rationale explaining the most distinctive choice (e.g. "Borrowed Geist's monochrome restraint + tabular numerics; kept Material 3 surface tinting for elevation in dark mode.").

## Example invocations

```
/mba-build-design-system system_name="lumina-ui" accent_hue=260 base_system="vercel-geist" framework="react" css_approach="tailwind-v4"
/mba-build-design-system system_name="helm-design" accent_hue=145 base_system="linear" framework="vue"
/mba-build-design-system system_name="legacy-ds" base_system="shadcn-ui" --legacy
```

## Definition of done

- [ ] `tokens.css` fully populated (color, spacing, type, radius, motion, z-index, shadow, breakpoints).
- [ ] Light + dark theming via `light-dark()` (or media-query fallback if `--legacy`).
- [ ] Minimum 8 primitives, each with all 8 states.
- [ ] Layout primitives in `utilities.css` (Stack / Cluster / Grid / Sidebar / Switcher / Cover).
- [ ] Modern reset applied.
- [ ] Docs page renders every primitive in every variant × every state.
- [ ] README with philosophy, install, basic usage.
- [ ] No hardcoded px / hex anywhere.
- [ ] `prefers-reduced-motion` honored globally.
- [ ] 1-paragraph design rationale.
