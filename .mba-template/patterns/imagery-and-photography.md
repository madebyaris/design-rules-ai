# Imagery & Photography

Most "AI-generated" web designs feel sterile because they have no real photography. They lean on icon grids, abstract gradients, or fake phone mockups. For many verticals, this is wrong.

This pattern covers: when photos are mandatory, how to source them, how to mark them up, aspect ratios, and what to do when no real photo exists.

---

## 1. When real photos are MANDATORY

If the brief is in any of these verticals, the hero **must** contain at least one real photograph. A phone mockup, dashboard screenshot, or icon grid is **not a substitute**:

- Retail / e-commerce / shops (pet, book, plant, gift, fashion, anything physical)
- Restaurant / café / bar / bakery
- Hospitality / hotel
- Health / wellness / clinic
- Salon / spa / barber / nails
- Fitness / gym / yoga / pilates
- Real estate / property
- Agency / portfolio (case study image)
- Pet services (grooming, sitting, daycare)
- Travel / destination
- Fashion / beauty / lifestyle

For these verticals, treat the hero photo as the *single most important design decision*. Pick it before writing the headline. The headline is written *to fit the photo*, not the other way around.

See `[../../../.cursor/rules/40-tone-and-vertical.mdc](../../../.cursor/rules/40-tone-and-vertical.mdc)` for the full vertical → mode → imagery matrix.

---

## 2. Sourcing — placeholder URL convention

For demo / portfolio output, use **Unsplash Source** URLs as placeholders. They work without an API key, return a real high-quality photo, and are easy for the user to swap.

### Pattern

```html
<img
  src="https://images.unsplash.com/photo-{id}?w=1600&q=80&auto=format&fit=crop"
  alt="{specific description of subject}"
  width="1600"
  height="900"
  loading="eager"
  fetchpriority="high">
```

### Curated photo IDs by vertical

Use a known good Unsplash photo ID rather than random search URLs (which can return broken images). Examples vetted for the common verticals:

| Vertical | Subject | Unsplash photo ID |
|---|---|---|
| Pet shop / dogs | Golden retriever puppy | `1543466835-00a7907e9de1` |
| Pet shop / cats | Tabby kitten | `1592194996308-7b43878e84a6` |
| Pet shop / store interior | Pet store aisle | `1583337130417-3346a1be7dee` |
| Pet shop / aquarium | Fish in tank | `1522069169874-c58ec4b76be5` |
| Bakery | Fresh bread / pastries | `1509440159596-0249088772ff` |
| Café | Latte art / café table | `1495474472287-4d71bcdd2085` |
| Restaurant | Plated dish | `1414235077428-338989a2e8c0` |
| Yoga / wellness | Studio interior | `1545205597-3d9d02c29597` |
| Fitness / gym | Lifting weights | `1571902943202-507ec2618e8f` |
| Salon | Hair styling | `1560066984-138dadb4c035` |
| Real estate | Modern home exterior | `1568605114967-8130f3a36994` |
| Agency / office | Workspace | `1497366216548-37526070297c` |

> Always verify the photo ID renders by visiting `https://unsplash.com/photos/{id}` before committing it. If unsure, use `https://source.unsplash.com/1600x900/?{topic}` as a safer fallback (e.g. `?puppy`, `?bakery`, `?yoga`).

### When the user supplies their own brand

If the user has shared brand photos or said "I'll provide photos", stub them as:

```html
<img src="/images/hero.jpg" alt="..." width="1600" height="900">
```

…and note in the rationale: "Hero image stubbed at `/images/hero.jpg` — replace with your photo (recommended dimensions: 1600 × 900, focus on {subject})."

---

## 3. Aspect ratios by use

| Use | Aspect | Example dimensions |
|---|---|---|
| Hero (full-bleed landscape) | 16:9 | 1600 × 900, 1920 × 1080 |
| Hero (split layout, image right) | 4:5 or 1:1 | 800 × 1000 |
| Product card (grid) | 1:1 or 4:5 | 600 × 600 / 600 × 750 |
| Feature accompaniment | 4:3 or 3:2 | 800 × 600 |
| Avatar (testimonial) | 1:1 | 96 × 96 |
| Gallery thumbnail | 1:1 | 400 × 400 |
| Story / portrait | 9:16 | 540 × 960 |

**Always set explicit `width` and `height`** to prevent layout shift (Core Web Vitals — CLS).

---

## 4. Markup — modern responsive images

For the hero, use `<picture>` with art direction (different crops at different breakpoints):

```html
<picture>
  <source media="(min-width: 1024px)"
          srcset="https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=2400&q=80&auto=format&fit=crop&ar=16:9 1x,
                  https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=3200&q=80&auto=format&fit=crop&ar=16:9 2x">
  <source media="(min-width: 640px)"
          srcset="https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=1280&q=80&auto=format&fit=crop&ar=4:3">
  <img src="https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=800&q=80&auto=format&fit=crop&ar=4:5"
       alt="A golden retriever puppy looking up at the camera in a sunlit pet store"
       width="1600" height="900"
       loading="eager"
       fetchpriority="high">
</picture>
```

For below-the-fold images, swap `loading="eager" fetchpriority="high"` for `loading="lazy"`.

---

## 5. Alt text — write specific, descriptive

Bad: `alt="puppy"` / `alt="hero image"` / `alt=""`
Good: `alt="A golden retriever puppy sniffing a bag of treats in a sunlit pet shop"`

Alt text is also a self-check — if you can't write a specific alt, your photo isn't specific enough.

For purely decorative images (background pattern, divider), use `alt=""` (empty, not omitted).

---

## 6. Hero overlay — keeping text readable on a photo

When the hero text sits **on top of** the photo (not next to it):

```css
.hero {
  position: relative;
  min-height: 70vh;
  display: grid;
  place-items: end start;
  padding: var(--space-12);
}

.hero img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}

/* Subtle gradient — protects text without darkening the whole image */
.hero::before {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    180deg,
    transparent 0%,
    transparent 40%,
    color-mix(in oklch, var(--color-bg) 70%, transparent) 100%
  );
  z-index: 1;
}

.hero-content { position: relative; z-index: 2; max-width: 50ch; color: white; }
```

Always test the hero with text on the **lightest** and **darkest** points of the photo. If the gradient isn't enough, add a subtle text-shadow: `text-shadow: 0 1px 2px rgb(0 0 0 / 0.3);` (use sparingly).

---

## 7. Product / category grid — image-first

For retail product cards, the photo is the focus. Text is small and lives below:

```html
<article class="product-card">
  <img src="..." alt="Brown leather collar with brass buckle" width="600" height="600">
  <h3>Classic Leather Collar</h3>
  <p class="price">$28</p>
</article>
```

```css
.product-card { display: flex; flex-direction: column; gap: var(--space-3); }
.product-card img {
  aspect-ratio: 1 / 1;
  width: 100%;
  object-fit: cover;
  border-radius: var(--radius-md);
}
.product-card h3 { font-size: var(--font-size-base); font-weight: 500; }
.product-card .price { font-size: var(--font-size-sm); color: var(--color-fg-muted); }
```

No hover lift. No shadow. The photo carries the visual weight.

---

## 8. AI escape hatches to avoid

| ❌ Don't | ✅ Do |
|---|---|
| Phone mockup hero on a non-app site | Real photo of the product, place, or people |
| Stock Font Awesome icon as "logo" | Text wordmark or no logo bar |
| Generic person silhouette as avatar | Real photo OR initials in colored circle |
| AI-generated illustration of an animal | Real photo from Unsplash |
| Empty `<div>` with `background: gray` "placeholder" | Real Unsplash URL |
| Repeating one stock image five times | Five distinct images, varied subjects |

---

## 9. Self-check before returning

- [ ] Hero contains a real photograph (not a mockup, not an icon grid, not a gradient) for verticals where it's mandatory?
- [ ] Every `<img>` has explicit `width` and `height`?
- [ ] Every `<img>` has a specific descriptive `alt` (or `alt=""` if decorative)?
- [ ] Hero image uses `loading="eager"` and `fetchpriority="high"`; below-fold uses `loading="lazy"`?
- [ ] Product/gallery photos are real (Unsplash URLs or user-supplied), not AI-generated illustrations?
- [ ] No phone mockup posing as the hero of a non-app website?
