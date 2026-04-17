# Dark Mode

Dark mode is not "light mode with inverted colors". It needs different contrast curves, different shadows, and different accent saturations.

---

## The modern way: `light-dark()` + `color-scheme`

The 2026 default. One source, both themes. No JavaScript needed for system-pref dark mode.

```css
:root {
  color-scheme: light dark;

  --color-bg: light-dark(white, black);
  --color-fg: light-dark(black, white);
  --color-border: light-dark(#e5e5e5, #2a2a2a);
}
```

How it works:
- `color-scheme: light dark` opts the document into native theming (form controls, scrollbars, etc.).
- `light-dark(LIGHT, DARK)` resolves at runtime based on the active scheme.
- The active scheme follows `prefers-color-scheme` by default.

Manual override:

```html
<html data-theme="dark">
```
```css
[data-theme="light"] { color-scheme: light; }
[data-theme="dark"]  { color-scheme: dark; }
```

---

## Theme toggle (3 states recommended)

Users want: System / Light / Dark.

```js
function setTheme(theme) {
  // theme: 'system' | 'light' | 'dark'
  if (theme === 'system') {
    document.documentElement.removeAttribute('data-theme');
    localStorage.removeItem('theme');
  } else {
    document.documentElement.dataset.theme = theme;
    localStorage.setItem('theme', theme);
  }
}

// On load, restore preference
const saved = localStorage.getItem('theme');
if (saved) document.documentElement.dataset.theme = saved;
```

To avoid FOUC (flash of wrong theme), inline this in `<head>` before any CSS loads.

---

## Avoid pure black and pure white

| Surface | Light mode | Dark mode |
|---------|-----------|-----------|
| Page bg | `oklch(1 0 0)` (white) | `oklch(0.145 0 0)` (near-black, NOT pure) |
| Card bg | `oklch(0.985 0 0)` | `oklch(0.205 0 0)` |
| Border | `oklch(0.922 0 0)` | `oklch(0.269 0 0)` |
| Body text | `oklch(0.145 0 0)` | `oklch(0.985 0 0)` |
| Muted text | `oklch(0.439 0 0)` | `oklch(0.708 0 0)` |

Pure white text on pure black ("OLED black") creates halation and tires the eye. Use `oklch(0.985 0 0)` instead.

---

## Accent colors need MORE chroma in dark mode

A brand color tuned for white backgrounds (e.g. `oklch(0.546 0.215 262)` for indigo) looks dull on near-black. Bump lightness +0.05 to +0.1 and chroma slightly:

```css
--color-accent: light-dark(
  oklch(0.546 0.215 262),  /* light: rich indigo */
  oklch(0.62  0.188 260)   /* dark: brighter, less saturated */
);
```

OKLCH makes this a one-line tweak. Hex makes it a guessing game.

---

## Shadows mostly disappear in dark mode

Shadows on dark surfaces don't separate planes — the contrast against the dark bg is too low. Use **subtle borders** instead:

```css
.card { box-shadow: var(--shadow-sm); }

@media (prefers-color-scheme: dark) {
  .card {
    box-shadow: 0 0 0 1px color-mix(in oklch, var(--color-fg) 8%, transparent);
  }
}
```

Or use surface tinting (Material 3 approach): elevated surfaces get a slightly lighter bg.

---

## Images and screenshots

- Logos: provide both light and dark variants. Use `<picture>` with `prefers-color-scheme`:

```html
<picture>
  <source srcset="/logo-dark.svg" media="(prefers-color-scheme: dark)">
  <img src="/logo-light.svg" alt="Brand">
</picture>
```

- Screenshots: take dark-mode shots for dark mode pages. Don't show light-UI screenshots on a dark page.
- Photos: usually fine, but consider lowering contrast slightly with `filter: brightness(0.9)` if they look harsh.

---

## Code blocks

Code highlighting themes need their own switch. Use one light theme (e.g. GitHub Light) and one dark (e.g. GitHub Dark, Tokyo Night). Detect via `prefers-color-scheme` or class.

---

## Don't theme these

- Brand logos (use both variants).
- Embedded videos (handle their own UI).
- Third-party widgets (they manage themselves).
- User-uploaded content (preserve as-is).

---

## Test checklist

- [ ] Tested in `prefers-color-scheme: light` system setting.
- [ ] Tested in `prefers-color-scheme: dark` system setting.
- [ ] Manual theme override works without JS reload.
- [ ] No FOUC on initial page load (theme inlined in head).
- [ ] All text meets 4.5:1 contrast in both modes.
- [ ] Form controls (input, select, scrollbar) match the theme (covered by `color-scheme`).
- [ ] Logos swap correctly.
- [ ] Code blocks swap themes.
