# MBA Design Rules

**Generate UI/UX that looks professionally designed by humans, not AI.**

A complete Cursor-rules + commands + assets package that turns any LLM into a senior product designer at Linear / Vercel / Stripe — for free.

> New here? Skip the rest of this README and read **[GETTING-STARTED.md](./GETTING-STARTED.md)**.

---

## Mission

Stop AI-generated designs from looking AI-generated. Every element should be:

- **Intentional** — driven by an explicit rule, not improvisation.
- **Coherent** — every value comes from one canonical scale.
- **Accessible** — WCAG AA as the floor, not the ceiling.
- **Indistinguishable from human work** — would fit inside a real product codebase.

---

## What's in the box

```
.cursor/
├── rules/
│   ├── 00-design-principles.mdc      # taste + non-negotiables + self-critique
│   ├── 10-tokens-and-scales.mdc      # all approved values (single source)
│   ├── 50-components.mdc             # anatomy + 8-state matrix + density
│   ├── 60-pages-and-layouts.mdc      # primitives + archetypes + scan patterns
│   └── 95-platform-specific.mdc      # iOS / Android / desktop deltas (opt-in)
└── commands/
    ├── README.md                     # command index
    ├── mba-build-structure-skeleton.md
    ├── mba-build-design-system.md
    ├── mba-build-component.md
    ├── mba-build-landing-page.md
    └── mba-build-dashboard-page.md

.mba-template/
├── tokens/
│   ├── tokens-modern.css             # 2026: OKLCH, light-dark(), fluid type, container queries
│   └── tokens.css                    # 2025 legacy (back-compat)
├── patterns/
│   ├── landing-page-sections.md
│   ├── dashboard-layouts.md
│   ├── container-queries.md
│   ├── view-transitions.md
│   └── dark-mode.md
├── design-systems/                   # each has overview.md + components.md
│   ├── shadcn-ui/, vercel-geist/, linear/
│   ├── material-design-3/, apple-hig/
│   ├── adobe-spectrum/, ibm-carbon/, microsoft-fluent-2/
├── examples/                         # full-page HTML demos
│   ├── button.html, card.html, form.html
│   ├── input.html, modal.html, table.html
│   ├── nav.html, empty-state.html, skeleton.html
├── content/sample-content.json       # realistic names, copy, numbers
├── platforms/                        # per-platform deep-dive (referenced by 95-rule)
├── anti-patterns/ai-generated-tells.md
├── QUICK-REFERENCE.md
└── ICON-QUICK-REFERENCE.md
```

---

## Install

Copy `.cursor/` and `.mba-template/` to your project root. That's it. Cursor picks them up automatically.

```bash
cp -r design-rules-ai/.cursor design-rules-ai/.mba-template /path/to/your/project/
```

---

## The 5 commands

| Command | Use it for | Detail |
|---------|-----------|--------|
| `/mba-build-structure-skeleton` | First command on a new repo | [→ docs](./.cursor/commands/mba-build-structure-skeleton.md) |
| `/mba-build-design-system` | Scaffold tokens + primitives + docs | [→ docs](./.cursor/commands/mba-build-design-system.md) |
| `/mba-build-component` | One production-ready component | [→ docs](./.cursor/commands/mba-build-component.md) |
| `/mba-build-landing-page` | Marketing landing, content-first | [→ docs](./.cursor/commands/mba-build-landing-page.md) |
| `/mba-build-dashboard-page` | Compact dashboard with all states | [→ docs](./.cursor/commands/mba-build-dashboard-page.md) |

All commands are **thin orchestrators**: they read the rules, plan, generate, self-critique, output. They never duplicate rule content.

Full index: [`.cursor/commands/README.md`](./.cursor/commands/README.md).

---

## Where rules + values live (don't duplicate)

| You want… | Read… |
|-----------|-------|
| Design principles, taste, self-critique | [`.cursor/rules/00-design-principles.mdc`](./.cursor/rules/00-design-principles.mdc) |
| Spacing / type / color / radius / motion / z-index / shadow | [`.cursor/rules/10-tokens-and-scales.mdc`](./.cursor/rules/10-tokens-and-scales.mdc) |
| Component anatomy + 8 required states | [`.cursor/rules/50-components.mdc`](./.cursor/rules/50-components.mdc) |
| Page archetypes + layout primitives | [`.cursor/rules/60-pages-and-layouts.mdc`](./.cursor/rules/60-pages-and-layouts.mdc) |
| iOS / Android / desktop deltas | [`.cursor/rules/95-platform-specific.mdc`](./.cursor/rules/95-platform-specific.mdc) |
| Approved values as CSS variables (modern) | [`.mba-template/tokens/tokens-modern.css`](./.mba-template/tokens/tokens-modern.css) |
| Realistic names, companies, copy | [`.mba-template/content/sample-content.json`](./.mba-template/content/sample-content.json) |
| What NOT to do | [`.mba-template/anti-patterns/ai-generated-tells.md`](./.mba-template/anti-patterns/ai-generated-tells.md) |
| Working HTML examples per primitive | [`.mba-template/examples/`](./.mba-template/examples/) |

This README intentionally **does not** restate the token tables, anti-patterns, or accessibility requirements. They live in the rules. One source of truth.

---

## What's new in 2026

- **Layered rules architecture** — `00-design-principles` (taste), `10-tokens-and-scales` (values), `50-components`, `60-pages-and-layouts`, `95-platform-specific`. Each is focused and ≤ 200 lines for tight context windows.
- **Self-critique loop** — `00-design-principles.mdc` makes the LLM grade its own output against 6 dimensions and revise once if any score < 4.
- **Modern token layer** ([`tokens-modern.css`](./.mba-template/tokens/tokens-modern.css)) — OKLCH color, `light-dark()` automatic theming, fluid typography via `clamp()`, `color-mix()` recipes, container query units, `view-transition-name` reservations, `@property` declarations.
- **Z-index, shadow, elevation** scales added to the canonical token list.
- **Layout primitives** — Stack / Cluster / Grid / Sidebar / Switcher / Cover (Every Layout vocabulary) baked into commands.
- **Density model** — every page commits to compact / comfortable / spacious; mixed densities are forbidden.
- **Patterns** populated — landing sections, dashboard layouts, container queries, view transitions, dark mode.
- **Per-system cheat sheets** — every `design-systems/*/components.md` says "what to copy from this system".
- **Examples expanded** — input, modal, table, nav, empty-state, skeleton (in addition to button / card / form).
- **Commands rewritten** as thin orchestrators with all references fixed (no more phantom rule files).

Legacy `tokens.css` is preserved for back-compat. Pass `--legacy` to commands to use it.

---

## Reference design systems

The eight systems we ship cheat sheets for, with one-line "what to copy":

| System | What to copy |
|--------|--------------|
| **shadcn/ui** | Composition primitives, Radix-backed accessibility, copy-paste model. |
| **Vercel Geist** | Monochrome restraint, mono numerics, calm motion. |
| **Linear** | Keyboard-first, command palette, instant transitions, ruthless density. |
| **Material 3** | Dynamic color, tonal palettes, surface tinting for elevation. |
| **Apple HIG** | Safe areas, Dynamic Type, depth via blur, system-color discipline. |
| **Adobe Spectrum** | Density-switching scales, strong i18n + a11y baseline. |
| **IBM Carbon** | 2x grid, IBM Plex, enterprise data tables. |
| **Fluent 2** | Acrylic/Mica materials, system-themed accents, Reveal effect. |

See [`.mba-template/design-systems/`](./.mba-template/design-systems/) for full details.

---

## License

Use freely in personal and commercial projects. Attribution appreciated, not required.

---

**Goal:** generate designs indistinguishable from work by a senior product designer at the company you'd most want to ship from.
