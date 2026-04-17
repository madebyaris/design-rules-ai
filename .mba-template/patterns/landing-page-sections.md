# Landing Page Sections — Anatomy

Density: **spacious**. Scan: **Z-pattern**. One primary CTA above the fold.

---

## Hero

**Job:** answer "what is this and why should I care" in <5 seconds.

**Anatomy:**
- Eyebrow (optional): 11–12px, all-caps label, accent color. Sets context ("Now in beta", "For engineering teams").
- Headline: H1, 32–48px (fluid: `clamp(2rem, 1.5rem + 2.5vw, 3rem)`), 700 weight, line-height 1.1. **≤ 60 characters.** State a benefit, not a feature.
- Subhead: 18–20px, `--color-fg-muted`, line-height 1.5. **1–2 sentences max.** Add the proof or context the headline implies.
- Primary CTA: large button, accent color, action verb ("Start free trial", "Get early access", "Book a demo"). Avoid "Click here", "Learn more", "Get started" (too generic).
- Secondary CTA (optional): ghost or text-only ("Watch demo", "View on GitHub"). Visually quieter than primary.
- Trust micro-copy: 12–14px, muted ("No credit card. 14-day trial." or "★★★★★ 4.8 on G2").
- Visual: product screenshot, illustration, or short loop video. Right side on desktop, below text on mobile.

**Height:** 60–80vh. Don't fill 100vh — users need a hint that more exists below.

**Don't:** stack two equally-sized CTAs side by side. Don't use Lorem-style filler "Transform your business with our innovative AI solution".

---

## Social proof

**Job:** validate that real organizations use this.

Pick **one** treatment per page (don't stack all three):

1. **Logo wall** — 4–8 customer logos, grayscale (`filter: grayscale(1) opacity(0.6)`), single row, equal heights, no borders. Use real-sounding company names from `content/sample-content.json`.
2. **Stats bar** — 3 metrics, large numbers (32–48px), small label below. e.g. "12,847 teams", "$2.4M tracked", "99.97% uptime".
3. **Anchor testimonial** — one large quote with photo, name, title, company. More credible than 5 small ones.

**Spacing:** sits flush against hero (no big gap), separates with subtle border or `--color-bg-subtle`.

---

## Features

**Job:** explain what the product does, in the user's words.

**Pattern:**
- Section heading: H2, "What you can do" or product-specific.
- Grid: 3 columns desktop, 2 tablet, 1 mobile. `grid-template-columns: repeat(auto-fit, minmax(260px, 1fr))`.
- Each cell:
  - Icon (32px, `--color-accent`, from icon library — never generated SVG).
  - Title: H3, 20–24px, semibold. **2–4 words.**
  - Description: 14–16px, `--color-fg-muted`, **2–3 sentences.**
- Padding: `--space-6` between cells, `--space-12` to `--space-16` section padding.

**Don't:** more than 6 features in one grid (cognitive overload). Split into multiple sections if needed.

---

## How it works

**Job:** show the flow / get-started path.

**Pattern:**
- 3 steps (4 max).
- Each step: large number (48–60px, ultra-light or outlined for elegance), title (H3), description (1 sentence), optional small illustration.
- Layout: horizontal row on desktop, vertical stack on mobile. Connect with a thin line/arrow on desktop.

---

## Testimonials

**Job:** social proof from a person, not a logo.

**Pattern:**
- 1 anchor testimonial (above-the-fold style) OR 3-up grid (equal weight).
- Each: quote (16–20px italic optional), photo (48px circular), name (semibold), title + company (muted).
- Quote length: 1–2 sentences. Long quotes get skipped.
- Sample names and titles from `content/sample-content.json`.

---

## Pricing (optional)

**Job:** remove the "how much does it cost" friction.

**Pattern:**
- 2–3 tiers (Free → Pro → Enterprise OR Starter → Team → Business).
- Recommended tier visually emphasized (border, slight scale, "Most popular" badge — pick ONE signal, not all three).
- Each tier:
  - Tier name (H3).
  - Price: large (32–48px). Specify period ("$29 / month"). Annual toggle if applicable.
  - 1-line description ("For solo creators").
  - Feature list: 5–8 items, check icon (success color) per item.
  - CTA button. Match emphasis to tier (recommended = primary, others = secondary).
- Layout: 3 equal columns on desktop, stacked on mobile.

**Don't:** invent fake pricing for a portfolio piece — use realistic SaaS numbers ($9, $29, $99, $499).

---

## FAQ

**Job:** preempt objections, reduce sales friction.

**Pattern:**
- Native `<details><summary>` accordions (free keyboard support, no JS needed).
- 5–8 questions. More = users assume bigger commitment.
- Question: 16px semibold. Answer: 14–16px, `--color-fg-muted`, line-height 1.6.
- Group related questions if you have >8.

**Question style:** write in the user's voice ("Can I cancel anytime?" not "Cancellation policy").

---

## Final CTA

**Job:** capture users who scrolled all the way down.

**Pattern:**
- Cover primitive, full-width section.
- Background: contrasting (accent color tint, or dark band on light page).
- Heading: H2, action-oriented ("Ready to ship faster?").
- 1–2 sentences of supporting copy.
- Primary CTA (same text or stronger version of hero CTA).
- Trust micro-copy below.

---

## Footer

**Job:** structural, not decorative.

**Pattern:**
- 3–5 columns of links: Product, Company, Resources, Legal, optional Social.
- Each column: small uppercase label (12px, 600, letter-spacing 0.06em) + 4–6 link items (14px).
- Bottom row: logo, copyright, social icons (link to real socials, not placeholders).
- `--color-bg-subtle` background to delineate from page.

---

## Section spacing rhythm (vertical)

| Between | Spacing |
|---------|---------|
| Hero → social proof | `--space-12` to `--space-16` (or 0 if flush) |
| Major sections | `--space-16` to `--space-24` |
| Section heading → content | `--space-8` to `--space-12` |
| Subsection inside section | `--space-8` |
| Card → card | `--space-6` |

Consistency matters more than the exact values. Pick once, stick to it.
