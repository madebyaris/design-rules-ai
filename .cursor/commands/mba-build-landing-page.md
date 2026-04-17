---
name: mba-build-landing-page
description: Generate a content-first marketing landing page using MBA design rules
---

# MBA Build Landing Page

Generate a complete marketing landing page. **Content-first**: write what the product *does* before designing the layout.

## Arguments

- `product_name` (required) — e.g. "Lumina Invoicing".
- `industry` (optional, default `saas`) — `saas` | `developer-tools` | `fintech` | `analytics` | `ecommerce` | `health` | `creative` | `b2b` | `consumer`.
- `sections` (optional) — comma-separated. Default `hero,social-proof,features,how-it-works,pricing,faq,cta`.
- `system` (optional, default `vercel-geist`) — design system to emulate.
- `cta_text` (optional, default `Start free`) — primary CTA text.
- `framework` (optional, default `html`) — `html` | `react` (Next.js page) | `astro`.

## Procedure

### 1. READ the rules

- `[.cursor/rules/00-design-principles.mdc](mdc:.cursor/rules/00-design-principles.mdc)` — Layer A principles, especially "content sets the layout".
- `[.cursor/rules/10-tokens-and-scales.mdc](mdc:.cursor/rules/10-tokens-and-scales.mdc)` — values to use.
- `[.cursor/rules/60-pages-and-layouts.mdc](mdc:.cursor/rules/60-pages-and-layouts.mdc)` — landing archetype, Z-pattern scan, density rules.

### 2. READ the references

- `[.mba-template/patterns/landing-page-sections.md](mdc:.mba-template/patterns/landing-page-sections.md)` — anatomy of every section.
- `[.mba-template/design-systems/{system}/components.md](mdc:.mba-template/design-systems/)` — borrowed look + feel.
- `[.mba-template/content/sample-content.json](mdc:.mba-template/content/sample-content.json)` — names, companies, testimonials, copy snippets. **Use these.** Never "Acme Corp" or "John Doe".

### 3. CONTENT FIRST (write before designing)

Before any markup, write these out in plain text:

1. **One-sentence product description** — "Lumina helps freelancers send polished invoices and get paid in 1 click." Write this honestly. Don't pad it.
2. **Headline** — derived from #1. ≤ 60 characters. Benefit, not feature. ("Get paid faster, not later." — not "AI-powered invoicing platform".)
3. **Subhead** — 1–2 sentences expanding the headline. Concrete proof or context.
4. **Primary CTA** — action verb. "Start free", "Try the demo", "Book a call". NOT "Get started", "Click here", "Learn more".
5. **3 features** — each with: 2-word title, 1-sentence description. Use the user's words, not yours.
6. **3 testimonial sources** — pull names from `sample-content.json`, write believable quotes specific to the product.
7. **Pricing** (if included) — 2–3 tiers, realistic prices ($9 / $29 / $99 or $19 / $49 / Custom), real feature lists.

Only AFTER #1–7 are written, start markup. The layout serves the content.

### 4. PLAN the layout

Apply rules from `60-pages-and-layouts.mdc`:

- Density: **spacious** (24px base, 16–18px body, 80–96px section padding).
- Scan: **Z-pattern**.
- Focal point: ONE primary CTA above the fold. Secondary CTA visually quieter.
- Section order from `sections` arg, default order:
  1. Header / nav (sticky, transparent over hero)
  2. Hero (60–80vh)
  3. Social proof (logos OR stats OR anchor testimonial — pick one)
  4. Features (3-column grid)
  5. How it works (3 steps)
  6. Testimonials (1 anchor or 3-up)
  7. Pricing (optional)
  8. FAQ (`<details>` accordions)
  9. Final CTA
  10. Footer

### 5. GENERATE

Output structure:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{product_name} — {one-sentence-from-step-3}</title>
  <meta name="description" content="{step-3-#1}">
  <link rel="stylesheet" href="./styles.css">
</head>
<body>
  <header><nav class="topnav">...</nav></header>
  <main>
    <section class="hero">...</section>
    <section class="social-proof">...</section>
    <section class="features">...</section>
    <section class="how-it-works">...</section>
    <section class="testimonials">...</section>
    <section class="pricing">...</section>
    <section class="faq">...</section>
    <section class="cta">...</section>
  </main>
  <footer>...</footer>
</body>
</html>
```

CSS uses tokens from `[.mba-template/tokens/tokens-modern.css](mdc:.mba-template/tokens/tokens-modern.css)`. Import it at the top of the stylesheet OR inline its variables.

### 6. SELF-CRITIQUE (Layer C)

Score 1–5 on each. If any < 4, revise once.

- Hierarchy — primary CTA wins above the fold?
- Restraint — could you remove a section, gradient, or graphic and lose nothing?
- Rhythm — every value from `10-tokens-and-scales.mdc`?
- Content fit — copy reads like a real product, not generic SaaS-speak?
- Accessibility — semantic landmarks, heading hierarchy intact, focus-visible everywhere, real `<label>`s, alt text?
- Reference — would this look at home alongside Vercel / Stripe / Linear marketing pages?

Then run the `60-pages-and-layouts.mdc` §8 self-check.

### 7. OUTPUT

| Framework | Files |
|-----------|-------|
| `html` | `pages/landing.html`, `pages/landing.css` |
| `react` (Next.js App Router) | `app/page.tsx`, `app/page.module.css` (or Tailwind classes) |
| `astro` | `src/pages/index.astro` |

End with a 1-paragraph rationale: design system emulated, the one most distinctive choice, and which testimonial / stat carries the most weight.

## Anti-patterns to avoid

| ❌ | ✅ |
|----|----|
| Lorem ipsum | Real, specific, industry-appropriate copy |
| "Click here" / "Get started" CTA | Action verbs: "Start free", "Try the demo" |
| Two equally-weighted CTAs | One primary, one secondary (visually quieter) |
| Centered body text | Left-align body. Center only headlines and hero copy. |
| 6+ feature cells | 3, max 4. Cognitive overload above that. |
| "Acme", "John Doe", `user@example.com` | Names from `sample-content.json` |
| Perfect round numbers ($1,000) | Realistic ($1,247, +12.4%) |
| Centered logo wall with 12 logos | 4–8 logos, grayscale, single row |
| Generated `<svg>` paths | Icon library (Font Awesome, Lucide, Heroicons) |
| Heavy gradients on every section | One subtle gradient max, used as anchor |

## Example invocations

```
/mba-build-landing-page product_name="Lumina Invoicing" industry="fintech" system="vercel-geist" cta_text="Start free"
/mba-build-landing-page product_name="Helm CI" industry="developer-tools" sections="hero,features,how-it-works,cta" framework="astro"
```

## Definition of done

- [ ] Steps 3.1–3.7 written out before any markup.
- [ ] Hero has ONE primary CTA above the fold.
- [ ] Section spacing rhythm consistent (one scale value per gap type).
- [ ] All copy from `sample-content.json` or written specifically — no generic "leverage AI" filler.
- [ ] Realistic numbers, names, testimonials.
- [ ] Mobile layout tested mentally (single column, stacked sections).
- [ ] Heading hierarchy: one H1 in hero, then H2 per section, H3 inside.
- [ ] Footer has 3–5 link columns + copyright + social.
- [ ] 1-paragraph rationale written.
