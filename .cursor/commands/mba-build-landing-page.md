---
name: mba-build-landing-page
description: Generate a content-first marketing landing page using MBA design rules. Auto-detects vertical (SaaS vs retail/hospitality/wellness) and adapts skeleton, mode, and reference system accordingly.
---

# MBA Build Landing Page

Generate a complete marketing landing page. **Vertical-first, content-first**: classify the business, pick the right skeleton, then write the content, then design.

## Arguments

- `product_name` (required) — e.g. `"PawMart Pet Shop"`, `"Lumina Invoicing"`, `"Sage & Stem Yoga"`.
- `industry` (optional, default `auto`) — `auto` | `saas` | `dev-tools` | `fintech` | `analytics` | `b2b` | `consumer-app` | `retail` | `pet-shop` | `restaurant` | `cafe` | `wellness` | `salon` | `clinic` | `fitness` | `agency` | `real-estate` | `education` | `kids` | `luxury` | `creative`. When `auto`, the command infers from `product_name`.
- `mode` (optional, default `auto`) — `auto` | `light` | `dark` | `system`. When `auto`, picks per vertical (see [40-tone-and-vertical.mdc §3](mdc:.cursor/rules/40-tone-and-vertical.mdc)).
- `system` (optional, default `auto`) — design system to emulate. When `auto`, picks per vertical. Manual options: `vercel-geist` | `linear` | `shadcn-ui` | `apple-hig` | `material-design-3` | `ibm-carbon` | `microsoft-fluent-2` | `adobe-spectrum` | `custom-warm` | `custom-editorial`.
- `sections` (optional) — comma-separated. Default depends on vertical (SaaS vs local-business — see Step 0).
- `cta_text` (optional) — primary CTA. When omitted, picks per vertical (see Step 0). Avoid generic defaults.
- `framework` (optional, default `html`) — `html` | `react` | `astro`.

## Procedure

### 0. CLASSIFY THE VERTICAL (do this FIRST, before anything else)

Read `[.cursor/rules/40-tone-and-vertical.mdc](mdc:.cursor/rules/40-tone-and-vertical.mdc)` in full.

Then for THIS brief:

1. **Infer vertical** from `product_name` and any `industry` arg. Use the keyword table in `40-tone-and-vertical.mdc §1`. Examples:
   - `"PawMart Pet Shop"` → keyword `Shop` → vertical = **retail / pet-shop**
   - `"Lumina Invoicing"` → keyword `Invoicing` → vertical = **fintech / SaaS**
   - `"Sage & Stem Yoga"` → keyword `Yoga` → vertical = **wellness / studio**
   - `"Forge CI"` → keyword `CI` → vertical = **dev-tools**

2. **Pick skeleton** from the vertical (see `40-tone-and-vertical.mdc §6`):
   - SaaS / dev-tools / fintech / B2B / consumer-app → **SaaS landing skeleton** (hero, social proof, features, how-it-works, pricing, FAQ, CTA, footer) — described in `[.mba-template/patterns/landing-page-sections.md](mdc:.mba-template/patterns/landing-page-sections.md)`.
   - Retail / pet-shop / restaurant / café / wellness / salon / clinic / fitness / real-estate / kids → **local-business skeleton** (hero with photo, products/categories OR services, about, visit-us, reviews, gallery, contact, footer) — described in `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` §5.
   - Agency / portfolio / luxury / creative → **editorial skeleton** (hero typography or full-bleed image, case studies/work grid, about, contact).

3. **Pick default mode** per `40-tone-and-vertical.mdc §3`:
   - Dev-tools, fintech, analytics, gym/fitness → `dark` allowed
   - Retail, hospitality, wellness, salon, clinic, kids, education, real-estate, agency-light → **`light` (dark mode is wrong here)**

4. **Pick reference system** per `40-tone-and-vertical.mdc §7`. If the user passed `system=` and it doesn't match the vertical, **override and warn in the rationale**. (E.g. `system=vercel-geist` for a pet shop → override to `apple-hig` or `custom-warm`.)

5. **Pick default CTA** by vertical:
   - SaaS / dev-tools → `Start free`, `Try the demo`, `Book a demo`
   - Retail / shop → `Shop now`, `Visit our store`, `Browse {category}`
   - Restaurant / café → `Book a table`, `See the menu`, `Order online`
   - Wellness / salon / clinic → `Book a class`, `Book an appointment`, `See our services`
   - Pet shop specifically → `Visit us`, `Shop online`, `Book grooming`
   - Agency / portfolio → `See our work`, `Start a project`
   - Fitness / gym → `Get a free trial week`, `Book a class`

6. **Decide imagery requirement** per `40-tone-and-vertical.mdc §4`. If the vertical is in the "imagery mandatory" list, the hero MUST have a real photograph — read `[.mba-template/patterns/imagery-and-photography.md](mdc:.mba-template/patterns/imagery-and-photography.md)` for the placeholder URL convention and curated photo IDs.

**Write out the classification explicitly before moving to Step 1.** Example:

```
Vertical: retail / pet-shop (keyword "Shop" in product_name)
Mode: light (warm — dark mode wrong for retail)
System: apple-hig + custom-warm palette (overriding vercel-geist default — wrong register)
Skeleton: local-business (NOT SaaS landing — no pricing tiers, no free trial)
Imagery: MANDATORY — real puppy/store photos from Unsplash
Default CTA: "Visit us" (NOT "Start free")
Sections: hero, products, services, about, visit-us, reviews, gallery, footer
```

If ANY of these feels wrong or ambiguous, ask the user one clarifying question before generating.

### 1. READ the rules

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — Layer A principles + the escape-hatches list at the bottom of Layer B.
- `[.cursor/rules/40-tone-and-vertical.mdc](mdc:.cursor/rules/40-tone-and-vertical.mdc)` — verify your Step 0 choices.
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — values to use.
- `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` — the archetype matching your skeleton choice.
- `[.cursor/rules/50-components.mdc](mdc:.cursor/rules/50-components.mdc)` — buttons (default size + 8 states), avatars (initials NOT `fa-user`), inputs.

### 2. READ the references

- For SaaS skeleton → `[.mba-template/patterns/landing-page-sections.md](mdc:.mba-template/patterns/landing-page-sections.md)`.
- For local-business skeleton → `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` §5 and `[.mba-template/examples/landing-retail.html](mdc:.mba-template/examples/landing-retail.html)`.
- If imagery is mandatory → `[.mba-template/patterns/imagery-and-photography.md](mdc:.mba-template/patterns/imagery-and-photography.md)`.
- `[.mba-template/design-systems/{system}/components.md](mdc:.mba-template/design-systems/)` for the chosen reference system.
- `[.mba-template/content/sample-content.json](mdc:.mba-template/content/sample-content.json)` — names, companies, copy snippets. **Use these.** Never `Acme`, `John Doe`, `user@example.com`.

### 3. CONTENT FIRST (write before designing)

Before any markup, write out in plain text:

1. **One-sentence business description** — "PawMart is a neighborhood pet shop on Bedford Avenue selling premium food, toys, and grooming for dogs and cats." Specific, honest, no marketing-ese.
2. **Headline** — derived from #1. ≤ 60 characters. For SaaS: a benefit ("Get paid faster, not later."). For retail: a warm one-liner that states what the place is and what feels good about it ("Everything your dog needs, in one warm shop on Bedford Ave.").
3. **Subhead** — 1–2 sentences expanding the headline with concrete proof or context.
4. **Primary CTA** — verb appropriate to the vertical (see Step 0.5).
5. **Featured items / sections content:**
   - SaaS: 3 features (2-word title + 1 sentence description each)
   - Retail: 4–8 product categories or featured products (name + photo subject + price range)
   - Restaurant: 3–5 menu highlights (dish name + 1-line description + price)
   - Wellness: 3–5 services (name + duration + price + 1-line description)
6. **Reviews / testimonials:** 1–3 with realistic local-customer voice. For pet/animal businesses, include the pet's name. Pull people-names from `sample-content.json`.
7. **Visit Us info (local-business only):** address, hours table, phone, ideally an embedded-map placeholder.
8. **Pricing tiers (SaaS only):** 2–3 tiers with realistic numbers. **Do NOT add this to a retail/local-business page.**

Only AFTER all applicable items are written do you start markup. The layout serves the content.

### 4. PLAN the layout

Apply rules from the chosen archetype:

- **Density:** spacious for both SaaS and retail.
- **Mode:** from Step 0.3.
- **Scan:** Z-pattern for SaaS hero, F-pattern for retail product/service grids.
- **Focal point:** ONE primary CTA above the fold. If a secondary CTA exists, it must be visually quieter by **at least two signals** (variant + size + no-icon — see `60-pages-and-layouts.mdc §2`).
- **Section order:** from `sections` arg if passed; otherwise default per vertical (Step 0.2).
- **Section vertical padding:** pick ONE value (e.g. `var(--space-20)`) and apply it to ALL major sections. No mix of `--space-16` / `--space-20` / `--space-24` on the same page.
- **Imagery:** if mandatory, plan the hero around the photo first, then write the headline to fit the photo's mood.

### 5. GENERATE

Output structure (HTML — adapt for React/Astro):

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{product_name} — {one-sentence-from-step-3.1}</title>
  <meta name="description" content="{step-3.1}">
  <link rel="stylesheet" href="./styles.css">
  <!-- icon library: Font Awesome / Lucide / Heroicons. NEVER inline SVG. -->
</head>
<body class="page-spacious" data-theme="{light|dark|auto}">
  <header><nav class="topnav">...</nav></header>
  <main>
    <!-- Sections from Step 0.2 / sections arg -->
  </main>
  <footer>...</footer>
</body>
</html>
```

CSS rules:
- **Token import — pick exactly one strategy and follow it strictly:**
  - **Strategy A (DEFAULT, recommended).** Emit a THIRD output file: copy `.mba-template/tokens/tokens-modern.css` verbatim into the SAME directory as the page CSS (e.g. if you write `test/landing.css`, also write `test/tokens-modern.css`). Then in `landing.css` use:
    ```css
    @import url('./tokens-modern.css');
    ```
    This is the only path that survives no matter where the user asks you to save the page.
  - **Strategy B (alternative).** Inline the variables you actually use directly at the top of the page CSS. No `@import`. Self-contained, zero broken-path risk. Use this for single-file demos.
  - **NEVER** emit `@import url('../tokens/tokens-modern.css')` or any other parent-relative path. The example file `landing-retail.html` uses that path because it physically lives next to `.mba-template/tokens/`; your generated file does not. Copy-pasting that line into `test/`, `app/`, `src/pages/`, etc. always 404s.
  - The same rule applies to `tokens.css` if you choose the legacy token file instead of `tokens-modern.css`.
- **Only semantic tokens** in component CSS (`var(--color-success)`, never `oklch(...)`, never `--success-500`).
- **No SVG anywhere** — not in markup, not in CSS data URIs. Use icon-font glyphs in pseudo-elements if needed.
- Buttons: define ALL 8 states (default, hover, focus-visible, active, disabled, loading; empty/error N/A) even if only default + hover render on this page.
- `.btn` (no size modifier) must resolve to `md` styles by default.
- Honor `prefers-reduced-motion`.

### 6. SELF-CRITIQUE (Layer C + tonal fit + escape hatches)

Score 1–5 on each. If any < 4, **throw out and revise once**. If "Tonal fit" is < 4, throw out completely and start from a different reference system.

| Dimension | Question | Pass = 4+ |
|---|---|---|
| **Tonal fit** | Does the visual register match the business? Pet shop ≠ fintech; restaurant ≠ CLI tool. | Register is correct |
| **Skeleton fit** | If this is a brick-and-mortar/retail/service business, did I use the local-business skeleton (NOT SaaS)? | Correct skeleton |
| **Imagery** | If imagery is mandatory for this vertical, is there at least one real photograph in the hero? | Yes, real photo |
| **Hierarchy** | Can a user identify the primary action in under 1 second? | Yes |
| **Secondary CTA** | If present, is it quieter by ≥2 signals (variant + size + no-icon)? | Yes |
| **Restraint** | Could I remove a section, gradient, or graphic and lose nothing? | No |
| **Rhythm** | Every spacing/radius/font value from the approved scale? All section paddings the same value? | 100% |
| **Content fit** | Real copy from `sample-content.json` or specifically written; vertical-appropriate (no "Start free" on a brick-and-mortar shop)? | Yes |
| **Accessibility** | Semantic landmarks, focus-visible, AA contrast, 44px touch targets, real labels, alt text? | All checked |
| **Reference fit** | Could this code live inside a top-tier site for THIS vertical (Apple for retail, Linear for dev tools, Squarespace for hospitality)? | Yes |

Then run the escape-hatches scan from `[00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` Layer C:
- [ ] Zero `data:image/svg+xml,...` data URIs?
- [ ] Zero raw `oklch(...)` / `#hex` / `rgb(...)` in component CSS?
- [ ] No generic person/cube/rocket icons posing as logos or avatars?
- [ ] No phone-mockup hero on a non-app site?
- [ ] No "Start free trial" CTA on a brick-and-mortar business?
- [ ] No two same-size CTAs side-by-side in the hero?
- [ ] Token `@import` resolves from the OUTPUT directory? (i.e. `./tokens-modern.css` next to the page CSS, OR variables inlined — never `../tokens/...`)

Then run the `60-pages-and-layouts.mdc §8` self-check.

### 7. OUTPUT

| Framework | Files (write ALL of them, in the SAME directory) |
|---|---|
| `html` | `landing.html`, `landing.css`, **`tokens-modern.css`** (copy from `.mba-template/tokens/`) |
| `react` (Next.js App Router) | `app/page.tsx`, `app/page.module.css` (or Tailwind classes), **`app/tokens-modern.css`** if you @import it |
| `astro` | `src/pages/index.astro`, **`src/pages/tokens-modern.css`** if you @import it |

If the user specifies a save location (e.g. `save it to @test`), all files go in THAT directory together. Never split the page CSS and the tokens CSS across directories — the @import must resolve as `./tokens-modern.css` from where the page CSS lives. (Strategy B from §5 is fine too: inline tokens, skip the third file entirely.)

**End with a 1-paragraph rationale containing:**
- Vertical you classified the brief into and why.
- Reference system you emulated (and any override of the user's `system=` arg).
- Whether real photography was mandatory and where you sourced it.
- The single most distinctive design choice you made.

## Anti-patterns to avoid

| ❌ | ✅ |
|----|----|
| Defaulting to SaaS skeleton for every brief | Classify vertical in Step 0; use local-business skeleton when appropriate |
| Defaulting to `vercel-geist` + dark mode for a pet shop / café / salon | Override to `apple-hig` / `custom-warm`, light mode |
| Phone mockup hero on a non-app site | Real photograph from Unsplash |
| `fa-user` testimonial avatar | Initials in colored circle, OR a real photo |
| Stock Font Awesome icons as fake company logos | Text wordmarks in small caps, or omit |
| `data:image/svg+xml,...` chevrons in CSS | Icon-font unicode (`content: "\f078"; font-family: "Font Awesome 6 Free";`) |
| Inline `oklch(0.55 0.17 162)` in component CSS | `var(--color-success)` |
| Two `btn-lg` buttons (primary + ghost) side by side | Primary lg + ghost md (no icon) OR text link |
| "Start free trial" + pricing tiers on a brick-and-mortar shop | "Visit us" + product grid + hours |
| Lorem ipsum / "Acme Corp" / "John Doe" | Real, vertical-appropriate copy |
| Mixed section padding (some `--space-16`, some `--space-20`) | One value applied to ALL major sections |
| `@import url('../tokens/tokens-modern.css')` copy-pasted from the example | Copy `tokens-modern.css` to the output dir + import `./tokens-modern.css`, or inline the variables |
| 6+ feature cells | 3, max 4 |
| Centered body text | Left-align body. Center only headlines and hero copy. |
| Heavy gradients on every section | One subtle gradient max, used as anchor |

## Example invocations

```
/mba-build-landing-page product_name="PawMart" industry="pet-shop"
/mba-build-landing-page product_name="Sage & Stem Yoga" industry="wellness"
/mba-build-landing-page product_name="Lumina Invoicing" industry="fintech"
/mba-build-landing-page product_name="Forge CI" industry="dev-tools" mode="dark"
/mba-build-landing-page product_name="Bedford Bakery" industry="cafe" framework="astro"
/mba-build-landing-page product_name="Atlas Studios" industry="agency" mode="light" system="custom-editorial"
```

When `industry` is omitted (`auto`), the model classifies from `product_name`. Be explicit if you want to skip the inference.

## Definition of done

- [ ] Step 0 classification written out explicitly (vertical, mode, system, skeleton, imagery, default CTA).
- [ ] Step 3 content (1.1–all applicable) written out before any markup.
- [ ] Skeleton matches vertical (SaaS landing for SaaS; local-business for retail/hospitality/wellness).
- [ ] Hero contains a real photograph if vertical requires it.
- [ ] Hero has ONE primary CTA above the fold; secondary (if any) is quieter by ≥2 signals.
- [ ] All major section paddings share a single value.
- [ ] All copy from `sample-content.json` or specifically written; vertical-appropriate.
- [ ] All buttons have all 8 states defined; `.btn` resolves to `md` by default.
- [ ] Avatars use initials OR real photos — never `fa-user`.
- [ ] Logo bar (if present) uses real wordmarks or text — never stock Font Awesome icons.
- [ ] Zero raw `oklch(...)` / `#hex` / `data:image/svg+xml` in component CSS.
- [ ] Heading hierarchy: one H1 in hero, then H2 per section, H3 inside.
- [ ] Footer has structural links + copyright + social.
- [ ] **Token import resolves locally:** either (a) a copy of `tokens-modern.css` is written into the SAME directory as the page CSS and the page CSS imports `./tokens-modern.css`, OR (b) the variables are inlined and there is no `@import`. NEVER `../tokens/...`.
- [ ] 1-paragraph rationale written including vertical classification.
