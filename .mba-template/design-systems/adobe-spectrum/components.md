# Adobe Spectrum — Components Cheat Sheet

**Canonical docs:** https://spectrum.adobe.com

**What to copy from this system:** rigorous accessibility, internationalization-first, dense desktop tooling patterns, scale-invariant components.

---

## When to choose Spectrum

- Desktop-class creative tools (Photoshop, Premiere, XD style).
- Apps that prioritize i18n and a11y from day one.
- React-heavy apps (`@adobe/react-spectrum` is excellent).
- Density needs to switch between mouse (compact) and touch (medium).

---

## Defining traits

| Trait | How |
|-------|-----|
| **Two scales** | Medium (touch, 32px button) and Large (desktop dense, 24px button). Switch by platform. |
| **5 themes** | Light, Dark, Lightest, Darkest, plus Spectrum Express variants. |
| **Strong a11y baseline** | Built on React Aria — keyboard, screen reader, focus management for free. |
| **Tokenized everything** | Color, size, motion all expressed as tokens. Scale switching changes tokens, not components. |
| **i18n native** | RTL support, locale-aware date/number formatting, translatable strings. |

---

## Component patterns

| Component | Notable detail |
|-----------|---------------|
| **Action Button** | Compact, icon-focused, used in toolbars. |
| **Picker** | Spectrum's polished Select. Searchable variants. |
| **Combo Box** | Autocomplete + free input. |
| **Tag Group** | Chips with focus management for keyboard removal. |
| **Side Nav** | Multi-level with disclosure. |
| **Toast** | Uses ARIA live regions for screen reader announcements. |
| **Dialog** | Modal, alert, popover variants with proper focus trap. |
| **Color Picker** | Industry-grade color picker primitives. |

---

## Density switching

```jsx
import { Provider, defaultTheme } from '@adobe/react-spectrum';

<Provider theme={defaultTheme} scale="medium">  {/* or "large" */}
  <App />
</Provider>
```

`medium` = touch density (mobile/tablet), `large` = mouse density (desktop). Components automatically restyle.

---

## Tokens (selected)

```
color-base / color-accent / color-warning / color-negative / color-positive / color-informative
size-50 ... size-1000 (granular spacing scale)
border-radius-regular = 4px
animation-duration-100 = 130ms
```

Full spec: https://spectrum.adobe.com/page/design-tokens/

---

## Implementation

- React: `@adobe/react-spectrum` (full components) or `react-aria-components` (headless primitives).
- Web Components: `@spectrum-web-components`.
- Adobe-only internally — community can use the OSS bits.

---

## What to AVOID copying

- Don't apply Spectrum to consumer SaaS — it reads as "professional creative tool" and can feel cold for general audiences.
- Don't skip the scale switching — using only `medium` on desktop wastes screen space; only `large` on mobile breaks touch targets.
- Don't strip the React Aria foundation if you adopt the components — that's where the a11y lives.
- Don't try to recreate the icon library — it's proprietary. Use Lucide or Heroicons.
