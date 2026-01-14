# MBA Design Rules

**Generate UI/UX that looks professionally designed by humans, not AI.**

## 🎯 Mission

Stop AI-generated designs from looking like AI-generated designs. Every design decision should be:
- **Intentional**: Based on established design systems
- **Consistent**: Following a coherent system
- **Accessible**: Meeting WCAG AA standards minimum
- **Professional**: Indistinguishable from human designers

## 📁 Project Structure

```
.cursor/
├── rules/
│   ├── mba-design-rules.mdc    # Core rules (spacing, colors, typography, etc.)
│   ├── 50-components.mdc       # Component patterns reference
│   ├── 60-pages-templates.mdc  # Page layout patterns
│   └── 95-platform-specific.mdc # iOS, Android, Desktop guidelines
└── commands/                    # Cursor chat commands

.mba-template/
├── tokens/
│   └── tokens.css              # ALL approved design values
├── content/
│   └── sample-content.json     # Realistic placeholder data
├── examples/                   # Working HTML component examples
│   ├── button.html
│   ├── card.html
│   └── form.html
├── design-systems/             # Reference patterns
│   ├── shadcn-ui/
│   ├── vercel-geist/
│   ├── linear/
│   ├── adobe-spectrum/
│   ├── material-design-3/
│   └── ...
├── platforms/                  # Platform-specific guidelines
├── anti-patterns/              # What NOT to do
└── QUICK-REFERENCE.md          # Copy-paste values
```

## 🚀 Quick Start

### 1. Install
Copy `.cursor/` and `.mba-template/` to your project root.

### 2. Use Commands
```
/mba-build-component component_name="button" framework="react"
/mba-build-landing-page product_name="My Product"
/mba-build-dashboard-page dashboard_name="Analytics"
```

### 3. Rules Apply Automatically
The `.cursor/rules/*.mdc` files guide AI when generating code.

## 📋 Critical Resources

| Resource | Path | Purpose |
|----------|------|---------|
| **Design Tokens** | `.mba-template/tokens/tokens.css` | ALL approved values |
| **Sample Content** | `.mba-template/content/sample-content.json` | Realistic data |
| **Quick Reference** | `.mba-template/QUICK-REFERENCE.md` | Copy-paste values |
| **Examples** | `.mba-template/examples/` | Working HTML |

## 🔢 Approved Values

### Spacing (ONLY these)
```
4px | 8px | 12px | 16px | 20px | 24px | 32px | 40px | 48px | 64px | 80px | 96px
```
**FORBIDDEN:** 7px, 13px, 19px, 23px, or ANY value not listed.

### Border Radius (ONLY these)
```
4px  - buttons, inputs
8px  - cards
12px - modals
9999px - pills/avatars ONLY
```

### Animation Durations
```
100ms - hover/focus
200ms - buttons/inputs
300ms - modals/drawers
500ms - page transitions
```

## 🚫 Anti-AI Patterns (NEVER DO)

| ❌ Never | ✅ Instead |
|----------|-----------|
| Generate SVG code | Use Font Awesome, Heroicons, Lucide |
| Random spacing (7px, 13px) | Use approved scale |
| Over-rounded corners (>16px) | 4px, 8px, 12px only |
| "Lorem ipsum" | Use sample-content.json |
| "John Doe", "Acme Corp" | Realistic names |
| All text centered | Left-align body text |
| Rainbow colors (8+) | 2-3 accent colors max |
| No hover/focus states | Clear interactive feedback |

## 🎨 Icon Setup (Font Awesome)

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

<button aria-label="Close">
  <i class="fa-solid fa-xmark" aria-hidden="true"></i>
</button>
```

**NEVER generate SVG code.** Always use icon libraries.

## ♿ Accessibility Requirements

| Requirement | Value |
|-------------|-------|
| Touch targets | 44px × 44px minimum |
| Focus outline | 2px solid, 2px offset |
| Contrast (body) | 4.5:1 |
| Contrast (large) | 3:1 |

## ✅ Quality Checklist

- [ ] Spacing uses approved scale only
- [ ] Colors from tokens.css only
- [ ] Icons from library (no generated SVG)
- [ ] Touch targets ≥ 44px
- [ ] Focus states visible (2px outline)
- [ ] Contrast ≥ 4.5:1
- [ ] Semantic HTML
- [ ] Real content (no Lorem ipsum)
- [ ] Reduced motion support

## 📚 Reference Design Systems

- **shadcn/ui** - Modern React standard
- **Vercel Geist** - Minimal, clean
- **Linear** - Gold standard for non-AI look
- **Material Design 3** - Google's system
- **Apple HIG** - iOS/macOS patterns

---

**Goal**: Generate designs indistinguishable from professional, human-crafted work.
