# Vercel Geist — Components Cheat Sheet

**Canonical docs:** https://vercel.com/geist

**What to copy from this system:** monochrome restraint, monospace numerics, dense developer-tool aesthetic, calm motion.

---

## When to choose Geist

- Developer tools, dashboards, admin panels.
- Marketing sites for technical audiences.
- You want "premium minimalism" — quiet chrome, content-first.
- Sans + mono pairing matters (Geist Sans + Geist Mono).

---

## Defining traits

| Trait | How |
|-------|-----|
| **Monochrome by default** | Mostly black/white/gray. Color only for status (success/warning/error) and brand accent. |
| **Geist Sans + Geist Mono** | Numbers, code, IDs use mono. Tabular numerals everywhere. |
| **Border over shadow** | Cards = 1px border, no shadow. Shadow only for floating elements. |
| **Subtle motion** | `cubic-bezier(0.16, 1, 0.3, 1)` ease-out, 200ms default. No bounces. |
| **Tight density** | Compact spacing, 13–14px body in dashboards. |
| **Focus on numbers** | Tabular numerals, right-aligned, prominent in metric cards. |

---

## Component patterns

| Component | Notable detail |
|-----------|----------------|
| **Button** | Sharp 6px radius, subtle hover bg shift (no scale), no shadow. |
| **Input** | 1px border, no shadow, focus = single 2px ring in fg color (not accent). |
| **Card** | 1px border, 8–12px radius, no shadow. Hover = border darkens slightly. |
| **Tabs** | Underline style only. 2px border-bottom on active. |
| **Toast** | Bottom-right, slides up + fades, 4s default. |
| **Code block** | Mono, line numbers, copy button revealed on hover. |
| **Diff** | Green/red block backgrounds, mono font, inline +/- markers. |

---

## Color palette

- Primary: pure black / pure white (NOT in dark mode — use near-black `oklch(0.145 0 0)`).
- Grays: 12-step ramp, evenly spaced in OKLCH lightness.
- Accent: typically blue (`oklch(0.55 0.22 240)`) but minimal usage — only for primary CTA, links, focus rings.
- Status: green/yellow/red, used as text + small dots, not large fills.

---

## Typography

```css
font-family: "Geist", -apple-system, BlinkMacSystemFont, sans-serif;
font-feature-settings: "ss01", "cv11"; /* alternate glyphs */
font-variant-numeric: tabular-nums;
```

For numbers in dashboards: always tabular nums. For IDs, hashes, code: Geist Mono.

---

## Layout

- Generous horizontal margins on marketing (max-width ~1200px).
- Tight, edge-to-edge on dashboards.
- Vertical rhythm via consistent spacing (8/16/24/32/48px).

---

## What to AVOID copying

- Don't add shadows everywhere — borders carry the visual structure.
- Don't use accent color liberally — it's spent on the primary action only.
- Don't use playful easing (back-out, elastic). Stay calm.
- Don't crowd marketing pages — Geist is dense in apps, spacious in marketing.
