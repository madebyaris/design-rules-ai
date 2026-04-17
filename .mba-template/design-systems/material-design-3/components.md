# Material Design 3 — Components Cheat Sheet

**Canonical docs:** https://m3.material.io

**What to copy from this system:** dynamic color (theme from wallpaper), tonal palettes, surface tinting for elevation, comprehensive component library.

---

## When to choose Material 3

- Android apps (default).
- Cross-platform apps that target Android first.
- You want a comprehensive, prescriptive system with first-party components.
- Dynamic color (Material You) is a feature of your product.

---

## Defining traits

| Trait | How |
|-------|-----|
| **Dynamic color** | Generate full palette from a single seed (often user wallpaper on Android 12+). |
| **Tonal palette** | 13 tones (0–100) per color role: primary, secondary, tertiary, error, neutral, neutral-variant. |
| **Surface tinting** | Elevation expressed as a tint of the primary color overlaid on the surface, not just shadow. |
| **State layers** | Hover/focus/pressed apply a translucent state-color layer on top of the component. |
| **Shape system** | 5 shape families (none / xs / sm / md / lg / xl / full) — most components use `sm` (4px) or `md` (8px). |
| **Type scale** | Display / Headline / Title / Body / Label, each with Large/Medium/Small. |

---

## Component patterns

| Component | Notable variants |
|-----------|-----------------|
| **Button** | Filled, Filled Tonal, Elevated, Outlined, Text. Plus FAB (Small/Medium/Large/Extended). |
| **Text field** | Filled or Outlined. Filled is the M3 default. |
| **Card** | Elevated, Filled, Outlined. |
| **Top app bar** | Center-aligned, Small (64dp), Medium (112dp), Large (152dp). |
| **Bottom app bar** | 80dp, with FAB and overflow. |
| **Navigation bar** | 80dp, 3–5 destinations. |
| **Navigation rail** | 80dp vertical (tablet/foldable). |
| **Navigation drawer** | Standard 360dp, Modal overlays. |
| **Snackbar** | Bottom-center, 1–3 lines, optional action. |
| **Dialog** | Basic, Full-screen, Date picker, Time picker. |

---

## Color roles

```css
:root {
  --md-sys-color-primary: ...;
  --md-sys-color-on-primary: ...;
  --md-sys-color-primary-container: ...;
  --md-sys-color-on-primary-container: ...;
  /* ...same for secondary, tertiary, error, surface, surface-variant, outline... */
}
```

Each role has an "on-" pair (text/icon color that goes on top of it) and a "-container" pair (lower-emphasis variant).

---

## Elevation (5 levels)

Level 0 (no elevation) → Level 5 (highest). Each level adds shadow + surface tint:

```
Level 0: surface
Level 1: surface + 5%  primary tint  (cards default)
Level 2: surface + 8%  primary tint  (elevated cards, FAB)
Level 3: surface + 11% primary tint  (modal sheets)
Level 4: surface + 12% primary tint  (nav drawers)
Level 5: surface + 14% primary tint  (top app bars on scroll)
```

Use the `surfaceContainerHigh` / `surfaceContainerHighest` color tokens in M3 — they encode the tint already.

---

## Touch targets

- Minimum 48dp × 48dp.
- Spacing 8dp between adjacent targets.

---

## Motion

- Standard easing: `cubic-bezier(0.2, 0, 0, 1)` (M3 emphasized standard).
- Durations: 50ms (instant) / 200ms (short) / 300ms (medium) / 500ms (long).
- Container transforms: shared-axis, fade-through, container-transform.

---

## Implementation

- **Compose (Android):** `MaterialTheme { Surface { ... } }` with M3 color scheme.
- **Web (Material Web):** `@material/web` package, web components.
- **Tailwind:** there are unofficial M3 plugins; for production prefer Material Web.

---

## What to AVOID copying

- Don't apply M3 to non-Android apps that look out of place — iOS users perceive Material as "the wrong system".
- Don't disable dynamic color without a strong reason — it's M3's signature.
- Don't mix M3 with iOS-style components (filled buttons + iOS bordered = visual chaos).
- Don't skip state layers — they're how M3 conveys interactivity.
