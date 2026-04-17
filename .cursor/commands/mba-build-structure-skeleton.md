---
name: mba-build-structure-skeleton
description: Bootstrap a new project skeleton wired to MBA design rules and tokens
---

# MBA Build Structure Skeleton

Bootstrap a new project's directory layout with: tokens wired in, base layout primitives, density classes, sample page, and modern reset. This is the **first command** to run on a new repo.

## Arguments

- `project_name` (required) — e.g. `lumina-app`.
- `framework` (required) — `vite-react-ts` | `next-app-router` | `vue-vite` | `svelte-kit` | `astro` | `plain-html`.
- `css_approach` (optional, default `tailwind-v4`) — `tailwind-v4` | `vanilla-css` | `css-modules` | `styled-components`.
- `system` (optional, default `shadcn-ui`) — design system to lean on for primitives.
- `with_dark_mode` (optional, default `true`) — wire up theme toggle infrastructure.
- `legacy` (optional flag) — use 2025 `tokens.css` instead of `tokens-modern.css`.

## Procedure

### 1. READ the rules

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — non-negotiables.
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — tokens to wire.
- `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` — layout primitives to scaffold.

### 2. READ the references

- `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)` — token starting point (default).
- `[.mba-template/tokens/tokens.css](mdc:.mba-template/tokens/tokens.css)` — legacy fallback (`--legacy`).
- `[.mba-template/patterns/dark-mode.md](mdc:.mba-template/patterns/dark-mode.md)` — theme toggle pattern.
- `[.mba-template/patterns/container-queries.md](mdc:.mba-template/patterns/container-queries.md)` — modern responsive pattern.

### 3. PLAN

Confirm:

1. Framework + bundler picks (Vite vs Webpack vs Turbopack auto-determined by framework choice).
2. CSS approach and how tokens get bridged (CSS vars only / Tailwind `@theme` / styled-components `theme.ts`).
3. Routing: file-based (Next/Astro/SvelteKit) or app-defined (Vite-React).
4. Theme: light only / `light-dark()` / system + manual toggle.
5. First page to scaffold (typically a "Home" with a hero + dashboard link).

### 4. GENERATE — by framework

#### `vite-react-ts`

```
{project_name}/
├── package.json                  # vite, react, typescript, optional tailwind
├── vite.config.ts
├── tsconfig.json
├── index.html
├── src/
│   ├── main.tsx
│   ├── App.tsx
│   ├── routes/                   # if using react-router
│   │   ├── Home.tsx
│   │   └── Dashboard.tsx
│   ├── components/
│   │   ├── ui/                   # primitives (Button, Card, Input)
│   │   └── layout/
│   │       ├── Stack.tsx
│   │       ├── Cluster.tsx
│   │       ├── Grid.tsx
│   │       ├── Sidebar.tsx
│   │       ├── Switcher.tsx
│   │       └── Cover.tsx
│   ├── styles/
│   │   ├── tokens.css            # copied/adapted from tokens-modern.css
│   │   ├── reset.css             # modern reset
│   │   ├── globals.css           # body defaults, focus-visible, density classes
│   │   └── utilities.css         # composable utility classes
│   └── lib/
│       └── theme.ts              # theme toggle if with_dark_mode
└── README.md
```

Use `npm create vite@latest {project_name} -- --template react-ts` as a starting hint, then layer the structure above.

#### `next-app-router`

```
{project_name}/
├── app/
│   ├── layout.tsx                # imports tokens + reset, sets <html data-theme>
│   ├── page.tsx                  # home
│   ├── dashboard/page.tsx
│   ├── globals.css               # tokens + reset + global styles
│   └── theme-provider.tsx        # if with_dark_mode (next-themes recommended)
├── components/
│   ├── ui/                       # primitives
│   └── layout/                   # Stack/Cluster/Grid/Sidebar/Switcher/Cover
├── tailwind.config.ts            # if tailwind-v4 (mostly empty, uses @theme in CSS)
├── package.json
└── README.md
```

Use `npx create-next-app@latest --typescript --app` as a starting hint.

#### `vue-vite`

```
{project_name}/
├── package.json
├── vite.config.ts
├── index.html
├── src/
│   ├── main.ts
│   ├── App.vue
│   ├── router.ts                 # if using vue-router
│   ├── pages/Home.vue
│   ├── components/ui/            # primitives
│   ├── components/layout/        # Stack/Cluster/etc.
│   └── styles/                   # tokens, reset, globals, utilities
└── README.md
```

#### `svelte-kit`

```
{project_name}/
├── package.json
├── svelte.config.js
├── src/
│   ├── routes/+layout.svelte
│   ├── routes/+page.svelte
│   ├── routes/dashboard/+page.svelte
│   ├── lib/
│   │   ├── components/ui/
│   │   └── components/layout/
│   └── app.css                   # tokens + reset + globals
└── README.md
```

#### `astro`

```
{project_name}/
├── package.json
├── astro.config.mjs
├── src/
│   ├── pages/index.astro
│   ├── pages/dashboard.astro
│   ├── layouts/BaseLayout.astro
│   ├── components/ui/            # can be Astro / React / Vue / Svelte
│   ├── components/layout/
│   └── styles/                   # tokens + reset + globals
└── README.md
```

#### `plain-html`

```
{project_name}/
├── index.html                    # home
├── pages/dashboard.html
├── styles/
│   ├── tokens.css
│   ├── reset.css
│   ├── globals.css
│   └── utilities.css
├── components/                   # HTML partials (button.html, card.html...)
└── README.md
```

### 5. GLOBALS to write

`globals.css` (every framework) should include:

```css
@import "./reset.css";
@import "./tokens.css";

html { -webkit-text-size-adjust: 100%; text-rendering: optimizeLegibility; }
body { font-family: var(--font-sans); color: var(--color-fg); background: var(--color-bg); line-height: 1.5; }
img, video, canvas { max-width: 100%; height: auto; display: block; }

:where(a, button, input, select, textarea, [tabindex]):focus-visible {
  outline: 2px solid var(--color-border-strong);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}

.page-compact     { --component-padding: var(--space-2); --component-row-h: 32px; --component-text: var(--font-size-sm); }
.page-comfortable { --component-padding: var(--space-4); --component-row-h: 40px; --component-text: var(--font-size-base); }
.page-spacious    { --component-padding: var(--space-6); --component-row-h: 48px; --component-text: var(--font-size-lg); }

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
}
```

### 6. DARK MODE wiring (if `with_dark_mode=true`)

- Inject inline `<head>` script to set `data-theme` from `localStorage.theme || 'system'` BEFORE first paint (avoids FOUC).
- Add a theme-toggle component: System / Light / Dark.
- Tokens use `light-dark()` (modern) — works automatically.

### 7. SELF-CRITIQUE (Layer C)

Score 1–5. Revise if any < 4.

- **Tokens reach every leaf** — no component bypasses the token system?
- **No hardcoded values** in any starter file?
- **Reset present and modern** (Andy Bell / Josh Comeau style)?
- **Layout primitives** scaffolded as components?
- **Dark mode** wired without FOUC (if requested)?
- **Sample page** demonstrates: heading hierarchy, button variants, a card, a layout primitive?

### 8. OUTPUT

Files exactly as in step 4 + a README explaining:

- Stack and why.
- How to run dev server.
- Where tokens live and how to extend them.
- How to add a primitive.
- Density classes and how to apply them.
- Dark mode toggle if applicable.

End with a 1-paragraph rationale: framework choice, CSS approach choice, and any opinionated decision (e.g. "using `light-dark()` over class-based dark mode for less JS").

## Example invocations

```
/mba-build-structure-skeleton project_name="lumina-app" framework="next-app-router" css_approach="tailwind-v4" system="vercel-geist"
/mba-build-structure-skeleton project_name="helm-tools" framework="vite-react-ts" css_approach="css-modules" system="linear"
/mba-build-structure-skeleton project_name="docs-site" framework="astro" with_dark_mode=true
/mba-build-structure-skeleton project_name="legacy-app" framework="plain-html" --legacy
```

## Definition of done

- [ ] Folder structure matches the framework's conventions.
- [ ] `tokens.css` (modern by default) wired in via globals or framework-equivalent.
- [ ] Modern CSS reset applied.
- [ ] Layout primitives (Stack/Cluster/Grid/Sidebar/Switcher/Cover) scaffolded.
- [ ] Density classes available (`page-compact`, `page-comfortable`, `page-spacious`).
- [ ] Focus-visible style applied globally.
- [ ] `prefers-reduced-motion` honored.
- [ ] Sample page renders without errors (button + card + heading).
- [ ] Dark mode toggle works without FOUC (if requested).
- [ ] README explains how to extend tokens and add primitives.
- [ ] 1-paragraph rationale.
