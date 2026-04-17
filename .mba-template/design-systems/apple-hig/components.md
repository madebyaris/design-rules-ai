# Apple HIG — Components Cheat Sheet

**Canonical docs:** https://developer.apple.com/design/human-interface-guidelines

**What to copy from this system:** safe area discipline, Dynamic Type, depth via blur and translucency, native gestures, restrained color.

---

## When to choose Apple HIG

- iOS, iPadOS, macOS, visionOS apps.
- Cross-platform apps where iOS quality matters most.
- You want native-feel SwiftUI/UIKit components.

---

## Defining traits

| Trait | How |
|-------|-----|
| **Safe areas** | Respect insets always. Use `safe-area-inset-*` (web) or `.safeAreaInset()` (SwiftUI). |
| **Dynamic Type** | Never fixed sizes. Use semantic styles (`.body`, `.headline`, `.caption`). |
| **System colors** | Adapt to light/dark/high-contrast automatically. Use `Color.label`, `.secondaryLabel`, `.systemBackground`. |
| **Translucency / vibrancy** | Bars, sheets, popovers use blur backdrop with vibrancy-shifted text. |
| **SF Symbols** | Use SF Symbols (5,000+ icons) as the icon language. Configurable weight, scale, color. |
| **Edge-swipe back** | Don't override the system back-swipe gesture. |
| **Tap, swipe, long-press, drag, pinch** | Standard gesture vocabulary — don't reinvent. |

---

## Component patterns

| Component | Notable detail |
|-----------|---------------|
| **Navigation bar** | 44pt compact, 96pt with large title. Auto-collapses to compact on scroll. |
| **Tab bar** | 49pt, 2–5 tabs. Always at bottom (iPhone). |
| **Toolbar** | 44pt at bottom, contextual to current view. |
| **Sheets** | Detents: `.medium`, `.large`. Dismissable via grabber + swipe. |
| **Buttons** | `.borderedProminent` (filled), `.bordered` (tinted), `.plain` (text), `.borderless`. |
| **Lists** | Inset grouped (default in iOS settings), Grouped, Plain. Use `List` in SwiftUI. |
| **Alerts** | 1–2 buttons. Title + message + actions. Destructive role for destructive actions. |
| **Action sheets** | Bottom sheet on iPhone, popover on iPad. Cancel button always present. |
| **Pickers** | Wheel (compact), inline, menu, segmented. Match to context. |

---

## Color

```css
/* Web equivalents using -apple-system tokens */
color: -apple-system-label;             /* primary text */
color: -apple-system-secondary-label;   /* secondary text */
background: -apple-system-grouped-background;
```

In SwiftUI:
```swift
Color(.label)
Color(.systemBackground)
Color(.systemBlue)  // iOS tint
```

System tint colors per platform: blue (iOS default), can be overridden per-app via `accentColor`.

---

## Typography

- **SF Pro** (UI), **SF Pro Display** (large titles), **New York** (serif), **SF Mono** (code).
- Web fallback: `-apple-system, BlinkMacSystemFont`.
- Always use semantic Dynamic Type styles. Never hardcode sizes.

```swift
Text("Hello").font(.body)         // 17pt, scales with Dynamic Type
Text("Title").font(.largeTitle)   // 34pt
```

---

## Depth via blur (not shadow)

- Sheets, popovers, navigation bars use translucent material backdrops:
  - `.regularMaterial`, `.thinMaterial`, `.thickMaterial`, `.ultraThinMaterial`.
- Web equivalent: `backdrop-filter: blur(20px) saturate(180%)`.
- Avoid heavy shadows — they look foreign on iOS.

---

## Touch targets

- Minimum 44pt × 44pt.
- Recommended 48pt for primary actions.

---

## What to AVOID copying

- Don't override safe areas to fill notch/home indicator (looks broken).
- Don't use Material elevation shadows on iOS — feels like an Android port.
- Don't disable Dynamic Type — accessibility regression.
- Don't use SF Symbols on non-Apple platforms (license restriction; use Lucide/Heroicons).
- Don't use bottom navigation that mimics Android's Material nav bar — use the iOS tab bar instead.
