# Microsoft Fluent 2 — Components Cheat Sheet

**Canonical docs:** https://fluent2.microsoft.design

**What to copy from this system:** depth via Acrylic/Mica materials, system-integrated theming, comprehensive cross-platform tokens, productivity-app patterns.

---

## When to choose Fluent 2

- Windows-first apps (WinUI 3, WPF, web apps targeting Windows users).
- Microsoft 365-style productivity tools.
- Apps that benefit from Acrylic/Mica window backgrounds (Teams, Outlook, Office).
- Cross-platform apps where Windows feels first-class.

---

## Defining traits

| Trait | How |
|-------|-----|
| **Materials (Acrylic, Mica)** | Translucent backgrounds with system blur. Mica picks up desktop wallpaper. |
| **Reveal effect** | Cursor-tracking highlight on hoverable surfaces (subtle gradient follows pointer). |
| **Depth via layering** | Layers stack with subtle elevation, not heavy shadows. |
| **Segoe UI Variable** | The Windows 11 system font — variable font with Display/Text/Small optical sizes. |
| **System theming** | Inherits Windows accent color and theme by default. |
| **Connected experiences** | Components designed to feel native across Web, Windows, iOS, Android. |

---

## Component patterns

| Component | Notable detail |
|-----------|---------------|
| **Button** | Primary, Secondary, Subtle, Outline, Transparent. Plus Compound (icon + text + meta). |
| **Menu** | Item, Group, Item with submenu, Checkbox, Radio. Keyboard nav full. |
| **Combobox** | Free input + dropdown, async data, virtualized for large lists. |
| **Drawer** | Inline (push content) or Overlay. Left/right edges. |
| **Card** | Filled, Outline, Subtle. Often combines with Reveal effect. |
| **Toast** | Bottom-right, stack, dismissible, intent variants (info/success/warning/error). |
| **Dialog** | Modal with focus trap, size variants, action buttons in footer. |
| **TreeView** | Expandable hierarchies, async load, drag-drop optional. |
| **DataGrid** | Sortable, resizable, virtualized, cell-edit, row-select. |

---

## Materials (web equivalents)

```css
/* Acrylic — translucent + blur */
.acrylic {
  background-color: color-mix(in oklch, var(--surface) 60%, transparent);
  backdrop-filter: blur(60px) saturate(125%);
}

/* Mica (Windows 11) — subtle, almost-flat with depth hint */
.mica {
  background-color: color-mix(in oklch, var(--surface) 80%, var(--accent) 5%);
}
```

Native Windows: use `MicaController` or `DesktopAcrylicController` in WinUI 3.

---

## Color

- System accent color (user's Windows accent, or app brand).
- Neutral foreground: `oklch(0.16 0 0)` light / `oklch(0.95 0 0)` dark.
- Semantic colors: `colorPaletteRedForeground1`, etc. (Fluent token names are verbose by design).
- Use `colorNeutralBackground{1,2,3,4,5}` for layered surfaces.

---

## Typography (Segoe UI Variable)

```css
font-family: "Segoe UI Variable", "Segoe UI", -apple-system, BlinkMacSystemFont, sans-serif;
font-feature-settings: "liga", "kern";
```

Optical sizes via `font-optical-sizing: auto`. Variable axes: weight (300–900), italic.

---

## Implementation

- React: `@fluentui/react-components` (Fluent UI v9, the current line).
- Web Components: `@fluentui/web-components` (Fluent UI 2 in standards-based components).
- Native Windows: WinUI 3 (XAML).
- React Native: `@fluentui/react-native`.

---

## What to AVOID copying

- Don't add Acrylic/Mica on web without considering performance (blur is GPU-heavy on mobile).
- Don't ship Reveal effect to a touch device (no cursor → no effect, just dead code).
- Don't use Fluent on Apple-platform apps — the depth language reads as Windows.
- Don't pile on multiple translucent layers — clarity drops fast.
