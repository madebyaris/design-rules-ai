# MBA Cursor Commands

Five thin orchestrators that read the rules in `.cursor/rules/` and assets in `.mba-template/`, then plan → generate → self-critique. Use them inside Cursor chat with `/command-name`.

## Index

| Command | Purpose | When to use |
|---------|---------|-------------|
| [`/mba-build-structure-skeleton`](./mba-build-structure-skeleton.md) | Bootstrap a new project: tokens wired, layout primitives, density classes, sample page. | First command on a fresh repo. |
| [`/mba-build-design-system`](./mba-build-design-system.md) | Scaffold a complete design system (tokens + primitives + docs page). | After skeleton, when you want a full DS in `~/{system_name}/`. |
| [`/mba-build-component`](./mba-build-component.md) | Generate ONE production-ready component with all 8 states. | Adding/upgrading a single primitive. |
| [`/mba-build-landing-page`](./mba-build-landing-page.md) | Content-first marketing landing page (hero → features → CTA → footer). | Marketing site, product launch, public-facing pages. |
| [`/mba-build-dashboard-page`](./mba-build-dashboard-page.md) | Compact-density data dashboard (KPIs, table, filters, states). | Internal app, admin panel, analytics view. |

## How they work (shared procedure)

Every command runs the same loop:

1. **READ** the relevant rules in `[.cursor/rules/](mdc:.cursor/rules/)` (principles, tokens, components, pages).
2. **READ** the relevant template assets in `[.mba-template/](mdc:.mba-template/)` (patterns, design-systems, examples, sample-content).
3. **PLAN** the design in 5 explicit lines (archetype, density, focal point, primary CTA, required states).
4. **GENERATE** code referencing tokens — no hardcoded values, no Lorem ipsum, no fake "Acme Corp" data.
5. **SELF-CRITIQUE** using the Layer C checklist from `[00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)`. Revise once if any score < 4.
6. **OUTPUT** code + a 1-paragraph design rationale.

This means rules and template assets are the source of truth; commands never duplicate that content.

## Recommended workflow for a new project

```
1. /mba-build-structure-skeleton project_name="..." framework="next-app-router"
2. /mba-build-design-system system_name="..." base_system="vercel-geist"
3. /mba-build-landing-page product_name="..." industry="saas"
4. /mba-build-dashboard-page dashboard_type="..." system="linear"
5. /mba-build-component component_name="combobox" framework="react"   ← add primitives as you need them
```

## Tips

- **Specify a `system`** (e.g. `linear`, `vercel-geist`, `shadcn-ui`) — without one, the LLM defaults to generic, and you'll feel the difference immediately.
- **Pick a density** (`compact` for dashboards, `comfortable` for SaaS apps, `spacious` for marketing) — mixed densities are the #1 AI tell.
- **Use the modern token layer** by default. Add `--legacy` only if you need <2024 browser support.
- **Read the rationale paragraph** the command emits — if it's vague, the design is probably vague too. Re-prompt.

## Files referenced

- Rules: `[.cursor/rules/](mdc:.cursor/rules/)` — `00-design-principles`, `10-tokens-and-scales`, `50-components`, `60-pages-and-layouts`, `95-platform-specific`.
- Tokens: `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)` (default), `[tokens.css](mdc:.mba-template/tokens/tokens.css)` (legacy).
- Patterns: `[.mba-template/patterns/](mdc:.mba-template/patterns/)` — landing sections, dashboard layouts, container queries, view transitions, dark mode.
- Design system references: `[.mba-template/design-systems/](mdc:.mba-template/design-systems/)`.
- Live examples: `[.mba-template/examples/](mdc:.mba-template/examples/)` — button, card, form, input, modal, table, nav, empty-state, skeleton.
- Sample data: `[.mba-template/content/sample-content.json](mdc:.mba-template/content/sample-content.json)`.
