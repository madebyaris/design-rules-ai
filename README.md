# MBA Design Rules & Commands

**Generate UI/UX that looks professionally designed by humans, not AI.**

This repository contains comprehensive Cursor rules and commands to help AI generate designs that are indistinguishable from professional, human-crafted interfaces. Based on patterns from Adobe Spectrum, IBM Carbon, Material Design 3, Apple HIG, and Microsoft Fluent 2.

## 🎯 Mission

Stop AI-generated designs from looking like AI-generated designs. Every design decision should be:
- **Intentional**: Based on established design systems
- **Consistent**: Following a coherent system
- **Accessible**: Meeting WCAG AA standards minimum
- **Professional**: Indistinguishable from human designers

## 📁 Project Structure

```
.cursor/
├── rules/              # Cursor .mdc rule files
│   ├── 00-core-principles.mdc
│   ├── 10-visual-hierarchy.mdc
│   ├── 20-typography.mdc
│   ├── 30-color-system.mdc
│   ├── 40-spacing-layout.mdc
│   ├── 50-components.mdc
│   ├── 60-pages-templates.mdc
│   ├── 70-accessibility.mdc
│   ├── 80-anti-ai-patterns.mdc
│   ├── 90-responsive-adaptive.mdc
│   └── 95-platform-specific.mdc
└── commands/           # Cursor chat commands
    ├── mba-build-structure-skeleton.md
    ├── mba-build-design-system.md
    ├── mba-build-component.md
    ├── mba-build-landing-page.md
    └── mba-build-dashboard-page.md

.mba-template/          # Reference materials
├── design-systems/     # Big tech design system patterns
│   ├── adobe-spectrum/
│   ├── ibm-carbon/
│   ├── material-design-3/
│   ├── apple-hig/
│   └── microsoft-fluent-2/
├── patterns/           # Design pattern references
├── platforms/          # Platform-specific guidelines
│   ├── web-responsive.md
│   ├── desktop-apps.md
│   ├── ios-mobile.md
│   └── android-mobile.md
└── anti-patterns/      # What NOT to do
    └── ai-generated-tells.md
```

## 🚀 Quick Start

### 1. Install in Your Project

Copy the `.cursor/` and `.mba-template/` directories to your project root.

### 2. Use Cursor Commands

In Cursor AI chat, use the slash commands:

```
/mba-build-structure-skeleton project_name="My App" platform="web"
/mba-build-design-system system_name="My Design System" theme="enterprise"
/mba-build-component component_name="button" framework="react"
/mba-build-landing-page product_name="My Product" industry="saas"
/mba-build-dashboard-page dashboard_name="Analytics Dashboard"
```

### 3. Rules Apply Automatically

The `.cursor/rules/*.mdc` files automatically guide AI when generating code in your project.

## 📚 Available Commands

### `/mba-build-structure-skeleton`
Generate complete project structure with proper setup.

**Arguments:**
- `project_name` (required)
- `platform`: web|desktop|ios|android (default: web)
- `framework`: html|react|vue|svelte (default: html)
- `css_approach`: vanilla-css|tailwind|css-modules (default: vanilla-css)

### `/mba-build-design-system`
Generate comprehensive design system with tokens and components.

**Arguments:**
- `system_name` (required)
- `theme`: enterprise|neutral|editorial|playful (default: enterprise)
- `base_unit`: 2|4|8 (spacing base in px, default: 8)
- `primary_color`: Hex color (default: #0078D4)
- `platform`: web|desktop|ios|android (default: web)

### `/mba-build-component`
Generate production-ready component with all states.

**Arguments:**
- `component_name` (required)
- `framework`: html|react|vue|svelte (default: html)
- `variants`: Comma-separated list
- `sizes`: small,medium,large (default: medium)
- `theme`: enterprise|neutral|editorial|playful (default: enterprise)

### `/mba-build-landing-page`
Generate complete landing page with realistic content.

**Arguments:**
- `product_name` (required)
- `industry`: analytics|fintech|saas|ecommerce (default: saas)
- `sections`: Comma-separated list (default: hero,social-proof,features,pricing,faq,cta)
- `theme`: enterprise|neutral|editorial|playful (default: neutral)
- `cta_text`: Call-to-action text (default: "Get Started")

### `/mba-build-dashboard-page`
Generate data-dense dashboard with realistic data.

**Arguments:**
- `dashboard_name` (required)
- `layout`: sidebar-left|sidebar-right|topbar-only (default: sidebar-left)
- `widgets`: metrics,chart,table,activity (default: metrics,chart,table)
- `theme`: enterprise|neutral|editorial|playful (default: enterprise)
- `data_type`: sales|analytics|admin|monitoring (default: analytics)

## 🎨 Design Themes

### Enterprise (Default)
- **Use for**: Data-dense applications, admin panels, dashboards
- **Characteristics**: Compact spacing, subdued colors, high information density
- **Spacing**: 2px or 4px base unit
- **Colors**: Neutral with limited accent
- **Typography**: Smaller sizes (14px body)

### Neutral
- **Use for**: Modern SaaS products, general applications
- **Characteristics**: Balanced spacing, clear contrast, modern feel
- **Spacing**: 8px base unit
- **Colors**: Neutral base with brand accent
- **Typography**: Standard sizes (16px body)

### Editorial
- **Use for**: Content-heavy sites, blogs, marketing pages
- **Characteristics**: Generous whitespace, typographic hierarchy
- **Spacing**: 8px base unit, larger sections
- **Colors**: Minimal, text-focused
- **Typography**: Larger sizes (18px body)

### Playful
- **Use for**: Consumer apps, creative tools, fun products
- **Characteristics**: Rounded corners, gradients (controlled), vibrant
- **Spacing**: 8px base unit
- **Colors**: More colorful, purposeful gradients
- **Typography**: Rounded fonts optional

## 🚫 Anti-AI Patterns (What to Avoid)

The system actively prevents common AI-generated design tells:

### Token-Wasting Patterns
- ❌ **Generating SVG code from scratch** (HUGE token waste)
  - ✅ Use Font Awesome, Heroicons, Lucide, Material Symbols instead
  - ✅ See `.cursor/rules/15-icons-assets.mdc` for icon library guide

### Visual Red Flags
- ❌ Excessive gradients everywhere
- ❌ Over-rounded corners (>16px on small elements)
- ❌ Random spacing (7px, 13px, 19px)
- ❌ Low contrast text (#999 on #FFF)
- ❌ Generic placeholders ("Lorem ipsum", "Click here")

### Layout Red Flags
- ❌ Everything centered
- ❌ Inconsistent component sizing
- ❌ No visual hierarchy
- ❌ Rainbow colors without purpose

### Content Red Flags
- ❌ Unrealistic data (all perfect numbers)
- ❌ No empty/error states
- ❌ Generic names ("John Doe" everywhere)

**See `.mba-template/anti-patterns/ai-generated-tells.md` for complete list.**

## 📖 Core Principles

### 1. Consistent Spacing System
Use ONE base unit (2px, 4px, or 8px) and stick to it.
```
8px base: 8, 16, 24, 32, 40, 48, 64, 96
```

### 2. Limited Color Palette
- 1 primary brand color
- 0-1 secondary accent
- 4 semantic colors (success, warning, error, info)
- 1 neutral gray scale (50-900)

### 3. Clear Typography Hierarchy
- Modular scale (1.25 or 1.333 ratio)
- 1-2 font families maximum
- Consistent weights (400, 500, 600, 700)

### 4. Semantic HTML
- Proper landmarks (header, nav, main, aside, footer)
- Correct heading hierarchy (H1 → H2 → H3)
- Semantic elements (button, not div with onclick)

### 5. Accessibility First
- WCAG AA minimum (4.5:1 contrast for text)
- Touch targets: 44px × 44px (mobile), 32px × 32px (desktop)
- Focus indicators: 2px outline, visible
- Keyboard navigation for all features

### 6. Real Content
- No "Lorem ipsum"
- Realistic company/product names
- Varied, plausible data
- Meaningful copy

### 7. Platform-Appropriate
- **Web**: Responsive, mobile-first
- **Desktop**: Keyboard shortcuts, window management
- **iOS**: Safe areas, Dynamic Type, SF Pro
- **Android**: Material Design 3, Roboto, dynamic color

## 🔍 Reference Design Systems

The rules are based on patterns from:

- **Adobe Spectrum**: 8px grid, semantic colors, component patterns
- **IBM Carbon**: 2px grid, productive vs expressive, layer system
- **Material Design 3**: Dynamic color, tonal palettes, elevation
- **Apple HIG**: SF Pro, Dynamic Type, platform conventions
- **Microsoft Fluent 2**: Color ramps, elevation, cross-platform

See `.mba-template/design-systems/` for detailed documentation.

## 🌐 Platform Support

### Web (Responsive)
- Mobile-first approach
- Breakpoints: 640px, 768px, 1024px, 1280px
- Touch targets: 44px minimum
- Responsive typography

### Desktop Apps (Electron/Tauri)
- Window management
- Keyboard shortcuts
- Native menus
- System integration

### iOS Mobile
- Safe area insets
- Dynamic Type support
- SF Pro typography
- iOS components (UIKit/SwiftUI)

### Android Mobile
- Material Design 3
- Dynamic color
- Roboto typography
- Material components

## 📝 Documentation

- **Getting Started**: This README
- **Command Usage**: See individual command files in `.cursor/commands/`
- **Icon Libraries**: `.cursor/rules/15-icons-assets.mdc` - **NEVER generate SVGs**
- **Design System Patterns**: `.mba-template/design-systems/`
- **Platform Guidelines**: `.mba-template/platforms/`
- **Anti-Patterns**: `.mba-template/anti-patterns/`

### Cursor Rules
- `00-core-principles.mdc`: Foundation
- `10-visual-hierarchy.mdc`: Size, weight, color hierarchy
- `15-icons-assets.mdc`: **Icon libraries (NEVER generate SVGs)**
- `20-typography.mdc`: Type system
- `30-color-system.mdc`: Colors and contrast
- `40-spacing-layout.mdc`: Spacing and layout
- `50-components.mdc`: Component patterns
- `60-pages-templates.mdc`: Page layouts
- `70-accessibility.mdc`: A11y requirements
- `80-anti-ai-patterns.mdc`: What to avoid
- `90-responsive-adaptive.mdc`: Responsive design
- `95-platform-specific.mdc`: iOS, Android, Desktop

## ✅ Quality Checklist

Before finalizing any design, verify:

- [ ] Spacing uses consistent scale (no random px values)
- [ ] Colors have semantic meaning
- [ ] Typography follows clear hierarchy
- [ ] Semantic HTML structure
- [ ] Real, purposeful content (no Lorem Ipsum)
- [ ] WCAG AA contrast ratios
- [ ] Touch targets meet minimum sizes
- [ ] Focus states visible
- [ ] Border radius consistent (2-3 values max)
- [ ] No obvious AI-generated tells
- [ ] Platform-appropriate patterns
- [ ] Internal consistency maintained

## 🤝 Contributing

This is a living system. To improve:

1. Add new design system references to `.mba-template/design-systems/`
2. Document new patterns in `.mba-template/patterns/`
3. Update rules in `.cursor/rules/` as needed
4. Add new commands to `.cursor/commands/`

## 📄 License

MIT License - Use freely in your projects.

## 🙏 Credits

Based on design systems from:
- Adobe (Spectrum)
- IBM (Carbon)
- Google (Material Design)
- Apple (Human Interface Guidelines)
- Microsoft (Fluent)

And countless hours studying what makes designs look professional vs AI-generated.

---

**Remember**: The goal is to generate designs that are indistinguishable from professional, human-crafted work. Every decision should be intentional, consistent, and grounded in established design systems.

