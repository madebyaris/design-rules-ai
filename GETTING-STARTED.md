# Getting Started

A practical walkthrough for using the MBA design rules in Cursor (or any agentic IDE that reads `.cursor/rules/`). About 10 minutes end-to-end.

---

## What this is

Five Cursor commands + five always-on rules + a shared template of tokens, patterns, and examples — designed to make any LLM (Opus 4, GPT-5, Gemini, Composer, smaller open-weight models) generate UI that doesn't look "AI-generated".

The rules cover **taste** (what makes great design — restraint, hierarchy, rhythm, depth) AND **guardrails** (the values, scales, semantic HTML, ARIA, and anti-patterns to avoid).

---

## Install

### Option 1 — Use directly in this repo

You're already here. Open in Cursor:

```bash
cursor /Volumes/app/self-project/design-rules-ai
```

### Option 2 — Drop into your own project

Copy these into your repo root:

```
.cursor/rules/         → guides every LLM action
.cursor/commands/      → /mba-* slash commands
.mba-template/         → tokens, patterns, examples, design-system references
```

That's it. Cursor picks up `.cursor/rules/` automatically. Commands appear in the chat command palette.

---

## The 4 always-on rules

| File | Purpose |
|------|---------|
| [`.cursor/rules/00-design-principles.mdc`](./.cursor/rules/00-design-principles.mdc) | Layered: principles (taste) + non-negotiables + self-critique loop. The most important rule. |
| [`.cursor/rules/10-tokens-and-scales.mdc`](./.cursor/rules/10-tokens-and-scales.mdc) | The complete list of approved values: spacing, type, color, radius, motion, z-index, shadow, breakpoints, density. |
| [`.cursor/rules/50-components.mdc`](./.cursor/rules/50-components.mdc) | Component anatomy framework + the 8-state matrix every interactive thing must have. |
| [`.cursor/rules/60-pages-and-layouts.mdc`](./.cursor/rules/60-pages-and-layouts.mdc) | Layout primitives (Stack/Cluster/Grid/Sidebar/Switcher/Cover) + page archetypes + density-per-archetype. |

Plus one opt-in:

| File | Purpose |
|------|---------|
| [`.cursor/rules/95-platform-specific.mdc`](./.cursor/rules/95-platform-specific.mdc) | Triggered only on iOS/Android/desktop tasks. Platform deltas only — does not duplicate core rules. |

---

## The 5 commands

| Command | Use it for |
|---------|-----------|
| [`/mba-build-structure-skeleton`](./.cursor/commands/mba-build-structure-skeleton.md) | First command on a fresh repo. Sets up tokens, layout primitives, density classes. |
| [`/mba-build-design-system`](./.cursor/commands/mba-build-design-system.md) | Scaffold a complete design system (tokens + 8+ primitives + docs page). |
| [`/mba-build-component`](./.cursor/commands/mba-build-component.md) | Generate ONE production-ready component with all 8 states. |
| [`/mba-build-landing-page`](./.cursor/commands/mba-build-landing-page.md) | Marketing landing page — content-first, Z-pattern scan. |
| [`/mba-build-dashboard-page`](./.cursor/commands/mba-build-dashboard-page.md) | Compact dashboard — KPIs, table, filters, all states defined. |

Every command follows the same loop: read rules → read template → plan → generate → self-critique → output. They are thin orchestrators, not duplicators of rule content.

See [`.cursor/commands/README.md`](./.cursor/commands/README.md) for the full index.

---

## Modern vs Legacy tokens

Two token layers ship in `.mba-template/tokens/`:

| File | Use when |
|------|----------|
| [`tokens-modern.css`](./.mba-template/tokens/tokens-modern.css) (DEFAULT) | You're targeting Chrome 123+, Safari 17.5+, Firefox 124+ (≈ 2026 evergreen). Adds OKLCH color, `light-dark()`, fluid type via `clamp()`, `color-mix()`, container query units, view transition reservations. |
| [`tokens.css`](./.mba-template/tokens/tokens.css) | You need <2024 browser support. Pre-OKLCH, manual dark-mode, fixed-size type. Stable but conservative. |

All 5 commands default to **modern**. Pass `--legacy` to switch.

---

## A real workflow walkthrough

Building a SaaS app called "Lumina Invoicing" from zero:

### 1. Scaffold the project

```
/mba-build-structure-skeleton project_name="lumina-app" framework="next-app-router" css_approach="tailwind-v4" system="vercel-geist"
```

You get: a Next.js App Router skeleton with Tailwind v4, modern tokens wired in, layout primitives, density classes, dark-mode toggle, and a sample home page.

### 2. Build the design system

```
/mba-build-design-system system_name="lumina-ui" accent_hue=260 base_system="vercel-geist" framework="react" css_approach="tailwind-v4"
```

You get: `lumina-ui/` with `tokens/`, `primitives/` (Button, Input, Card, Modal, Toast, etc.), layout utilities, docs page showing every primitive in every state.

### 3. Build the marketing landing

```
/mba-build-landing-page product_name="Lumina Invoicing" industry="fintech" system="vercel-geist" cta_text="Start free" framework="react"
```

You get: `app/page.tsx` with hero / social proof / features / pricing / FAQ / CTA / footer, using realistic copy (Sasha Patel, Marcus Okonkwo, etc.) from `sample-content.json`.

### 4. Build the dashboard

```
/mba-build-dashboard-page dashboard_type="finance" primary_view="table" shell="sidebar-main" system="linear" framework="react"
```

You get: `app/dashboard/page.tsx` with sidebar nav, KPIs (Balance, MRR, Burn, Runway), invoice table with all states (default / loading / empty / error), realistic transaction data.

### 5. Add a missing primitive

```
/mba-build-component component_name="combobox" framework="react" system="shadcn-ui"
```

You get: `components/ui/Combobox.tsx` with all 8 states, Radix UI / Headless UI primitive composition, full keyboard accessibility.

---

## Key design principles (the one-page summary)

From `00-design-principles.mdc`:

1. **Restraint over decoration** — every element earns its place.
2. **Hierarchy through contrast, not size alone** — weight + color + position before bigger fonts.
3. **Rhythm via a single scale** — one spacing/type/radius scale per project.
4. **Content sets the layout** — write real copy first, then design around it.
5. **Depth is earned** — shadows/elevation are signals, not polish.
6. **Reference a real system** — pick one (Linear / Geist / shadcn / Material 3 / HIG) and stay inside it.
7. **Boring on purpose** — quiet chrome, surprise lives in content and motion.

---

## Common AI-generated tells (avoid these)

| Visual | Layout | Content |
|--------|--------|---------|
| Excessive gradients (especially purple→blue) | Random spacing (7px, 13px, 19px) | Lorem Ipsum |
| Unnecessary shadows on every element | Centered everything | "Acme Corp", "John Doe", "user@example.com" |
| Overuse of glassmorphism / blurred bg | No clear focal point | Perfectly round numbers ($1,000.00, +10%) |
| Same border radius everywhere (8px on everything) | Two equally-weighted CTAs | Generic SaaS jargon ("leverage AI", "transform your business") |
| 5+ accent colors on one page | Mixed densities (compact table inside spacious page) | Decorative-only emoji and icons |
| Missing :focus-visible (or `outline:none` with no replacement) | Sidebars that don't collapse on mobile | Skeletons used for instant content |

Full list: [`.mba-template/anti-patterns/ai-generated-tells.md`](./.mba-template/anti-patterns/ai-generated-tells.md).

---

## Platform support

| Platform | Triggered by | What you get |
|----------|--------------|--------------|
| Web (responsive) | Default | Mobile-first, container queries, view transitions, dark mode via `light-dark()`. |
| Desktop apps | `electron`, `tauri`, `desktop` keywords | Custom title bar, keyboard shortcuts, mouse-density components, native menus. |
| iOS / iPadOS | `ios`, `iphone`, `swift`, `swiftui` keywords | Safe areas, SF Pro, Dynamic Type, native sheets, edge swipe. |
| Android | `android`, `material`, `kotlin`, `compose` keywords | Material 3 dynamic color, Roboto Flex, M3 surfaces, FAB patterns. |

The `95-platform-specific.mdc` rule is description-triggered — it fires automatically on platform-specific tasks, stays out of the way otherwise.

---

## Quick reference values (most-used)

```
Spacing  4 8 12 16 24 32 48 64 px
Radius   4 (controls) 8 (cards) 12 (modals) 9999 (pills)
Type     12 14 16 20 24 32 48 60 px (or fluid via clamp())
Touch    44px mobile · 32px desktop
Contrast 4.5:1 body · 3:1 large/UI
Motion   100ms hover · 200ms button · 300ms modal
Easing   cubic-bezier(0.16, 1, 0.3, 1) — ease-out, expressive
```

Full list: [`.cursor/rules/10-tokens-and-scales.mdc`](./.cursor/rules/10-tokens-and-scales.mdc).

---

## When the LLM goes off-script

Symptom → fix:

| The output… | Reason | Fix |
|-------------|--------|-----|
| …looks generic / "AI-ish" | No `system` arg specified | Re-run with `system="linear"` (or geist, shadcn-ui). |
| …has random px values | Skipped reading the tokens rule | Re-prompt: "Re-read `10-tokens-and-scales.mdc` and replace every hardcoded value." |
| …has Lorem / Acme / John Doe | Skipped sample-content | Re-prompt: "Pull names and copy from `.mba-template/content/sample-content.json`." |
| …missing focus-visible / hover difference | Common shortcut | Re-prompt: "Add the 8-state matrix from `50-components.mdc` §2." |
| …two competing CTAs | No focal point committed | Re-prompt: "Per `60-pages-and-layouts.mdc` §2, pick ONE primary action and demote the rest." |
| …doesn't look like the chosen design system | Skipped `design-systems/{system}/components.md` | Re-prompt: "Re-read `.mba-template/design-systems/{system}/components.md` and adjust." |

---

## Help & references

- [Linear Design](https://linear.app) — best-in-class app UI.
- [Vercel Geist](https://vercel.com/geist) — restraint and monochrome.
- [shadcn/ui](https://ui.shadcn.com) — composition primitives.
- [Material Design 3](https://m3.material.io) — dynamic color, Android.
- [Apple HIG](https://developer.apple.com/design/human-interface-guidelines) — Apple platforms.
- [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/).
- [Every Layout](https://every-layout.dev) — the layout primitives vocabulary used in `60-pages-and-layouts.mdc`.

---

## What's new (vs the 2025 baseline)

- **`00-design-principles.mdc`** — taste + non-negotiables + self-critique. Replaces the old `mba-design-rules.mdc`.
- **`10-tokens-and-scales.mdc`** — z-index scale, shadow scale, elevation system added.
- **`50-components.mdc`** — anatomy framework + 8-state matrix + density rule.
- **`60-pages-and-layouts.mdc`** — layout primitives (Stack/Cluster/Grid/Sidebar/Switcher/Cover) + density-per-archetype.
- **`95-platform-specific.mdc`** — switched to description-triggered, deltas only.
- **`tokens-modern.css`** — OKLCH, `light-dark()`, fluid typography, container queries, view transitions.
- **`patterns/`** — populated with landing sections, dashboard layouts, container queries, view transitions, dark mode.
- **`design-systems/*/components.md`** — what to copy from each system.
- **Examples expanded** — input, modal, table, nav, empty-state, skeleton added to button/card/form.
- **Commands** — rewritten as thin orchestrators (no rule-content duplication, all references fixed).

The legacy `tokens.css` stays for back-compat. Everything else is fair game to update.
