# Getting Started with MBA Design Rules

## What is This?

MBA Design Rules is a comprehensive system of Cursor rules and commands that helps AI generate professional, human-quality UI/UX designs. It prevents common "AI-generated" tells and ensures designs follow established patterns from big tech companies.

## Installation

### 1. Copy to Your Project

Copy these directories to your project root:
```
your-project/
├── .cursor/
│   ├── rules/
│   └── commands/
└── .mba-template/
```

### 2. That's It!

The rules automatically apply when you use Cursor AI in your project.

## Using Commands

In Cursor AI chat, type `/` to see available commands:

### Quick Examples

**Start a new project:**
```
/mba-build-structure-skeleton project_name="My App" platform="web" framework="react"
```

**Create a design system:**
```
/mba-build-design-system system_name="My Design System" theme="enterprise" primary_color="#0066CC"
```

**Build a component:**
```
/mba-build-component component_name="button" framework="react" variants="primary,secondary,ghost"
```

**Generate a landing page:**
```
/mba-build-landing-page product_name="Acme Analytics" industry="saas" sections="hero,features,pricing,cta"
```

**Create a dashboard:**
```
/mba-build-dashboard-page dashboard_name="Analytics Dashboard" widgets="metrics,chart,table"
```

## Understanding Themes

### Enterprise (Default for Dashboards)
Best for: Data-dense apps, admin panels, enterprise software
- Compact spacing (2px or 4px base)
- Subdued colors
- High information density
- Smaller typography (14px body)

### Neutral (Default for Landing Pages)
Best for: Modern SaaS, general applications
- Balanced spacing (8px base)
- Clear contrast
- Standard sizing
- 16px body text

### Editorial
Best for: Content sites, blogs, marketing
- Generous whitespace
- Typographic focus
- Larger text (18px body)
- Minimal chrome

### Playful
Best for: Consumer apps, creative tools
- Rounded corners
- Controlled gradients
- Vibrant colors
- Fun, approachable

## Key Principles

### 0. Use Icon Libraries (NEVER Generate SVGs)
**CRITICAL: This saves massive amounts of tokens!**

```html
✅ Use Font Awesome:
<i class="fa-solid fa-user"></i>

✅ Use Heroicons (React):
<UserIcon className="h-6 w-6" />

❌ NEVER generate SVG code:
<svg>...</svg> <!-- NO! -->
```

**See `.cursor/rules/15-icons-assets.mdc` for complete guide.**

Recommended libraries:
- **Font Awesome**: Most popular, 2000+ icons
- **Heroicons**: Modern, Tailwind ecosystem
- **Lucide**: Clean, consistent
- **Material Symbols**: Google's design system
- **Bootstrap Icons**: Versatile, 2000+ icons

### 1. Consistent Spacing
Always use a spacing scale. Never random values.
```
✅ 8, 16, 24, 32, 40, 48, 64
❌ 7, 13, 19, 23, 31
```

### 2. Limited Colors
- 1 primary brand color
- 4 semantic colors (success, warning, error, info)
- 1 neutral gray scale
```
✅ 6-7 color families total
❌ Rainbow (10+ colors)
```

### 3. Real Content
```
✅ "Acme Analytics Dashboard"
❌ "Lorem ipsum dolor sit amet"

✅ "$1,234.56" (realistic)
❌ "$1,000.00" (too perfect)
```

### 4. Accessibility
- WCAG AA minimum (4.5:1 contrast)
- Touch targets: 44px × 44px (mobile)
- Focus indicators: 2px outline
- Keyboard navigation

### 5. Semantic HTML
```html
✅ <button>Click Me</button>
❌ <div onclick="...">Click Me</div>

✅ <header>, <nav>, <main>, <footer>
❌ <div class="header">, <div class="nav">
```

## What Makes Designs Look AI-Generated?

### Visual Red Flags
- ❌ Excessive gradients everywhere
- ❌ Over-rounded corners (>16px on small elements)
- ❌ Random spacing (7px, 13px, 19px)
- ❌ Low contrast text
- ❌ Generic "Lorem ipsum" text

### Layout Red Flags
- ❌ Everything centered
- ❌ Inconsistent component sizes
- ❌ No visual hierarchy
- ❌ Rainbow colors

### Content Red Flags
- ❌ Perfect round numbers ($1,000, 100 users)
- ❌ No empty/error states
- ❌ "John Doe" everywhere

**The system automatically prevents these!**

## Platform Support

### Web (Responsive)
- Mobile-first approach
- Breakpoints: 640px, 768px, 1024px
- Touch targets: 44px minimum

### Desktop Apps
- Keyboard shortcuts
- Window management
- Native menus

### iOS Mobile
- Safe area insets
- Dynamic Type
- SF Pro font

### Android Mobile
- Material Design 3
- Dynamic color
- Roboto font

## Quick Reference

### Spacing Scale (8px base)
```
8, 16, 24, 32, 40, 48, 64, 96
```

### Typography Scale
```
12px, 14px, 16px, 20px, 24px, 32px, 40px, 48px
```

### Border Radius
```
4px, 8px, 12px, 16px (max for most elements)
```

### Button Heights
```
Small: 32px
Medium: 40px
Large: 48px
```

### Touch Targets
```
Mobile: 44px × 44px minimum
Desktop: 32px × 32px minimum
```

## Common Workflows

### Starting a New Project
1. `/mba-build-structure-skeleton` - Set up project
2. `/mba-build-design-system` - Create design system
3. `/mba-build-component` - Build components as needed
4. `/mba-build-landing-page` or `/mba-build-dashboard-page` - Create pages

### Adding to Existing Project
1. Copy `.cursor/` and `.mba-template/` to your project
2. Use commands to generate new components/pages
3. Rules automatically guide AI for all code generation

## Need Help?

### Documentation
- **README.md**: Complete overview
- **This file**: Quick start guide
- **.cursor/rules/**: Detailed rules for each topic
- **.mba-template/**: Reference materials and examples

### Rules Reference
- `00-core-principles.mdc`: Foundation
- `10-visual-hierarchy.mdc`: Size, weight, color hierarchy
- `20-typography.mdc`: Type system
- `30-color-system.mdc`: Colors and contrast
- `40-spacing-layout.mdc`: Spacing and layout
- `50-components.mdc`: Component patterns
- `60-pages-templates.mdc`: Page layouts
- `70-accessibility.mdc`: A11y requirements
- `80-anti-ai-patterns.mdc`: What to avoid
- `90-responsive-adaptive.mdc`: Responsive design
- `95-platform-specific.mdc`: iOS, Android, Desktop

### Design System References
- `.mba-template/design-systems/adobe-spectrum/`
- `.mba-template/design-systems/ibm-carbon/`
- `.mba-template/design-systems/material-design-3/`
- `.mba-template/design-systems/apple-hig/`
- `.mba-template/design-systems/microsoft-fluent-2/`

## Tips for Best Results

1. **Be Specific**: "button with primary, secondary, and ghost variants" not just "button"
2. **Use Real Names**: "Acme Analytics Dashboard" not "My Dashboard"
3. **Specify Platform**: web, desktop, ios, or android
4. **Choose Theme**: enterprise, neutral, editorial, or playful
5. **Review Output**: Check against quality checklist in README

## Quality Checklist

Before finalizing:
- [ ] Consistent spacing scale used
- [ ] Colors have semantic meaning
- [ ] Typography hierarchy clear
- [ ] Semantic HTML
- [ ] Real content (no Lorem Ipsum)
- [ ] WCAG AA contrast
- [ ] Touch targets adequate
- [ ] Focus states visible
- [ ] No AI-generated tells

## Next Steps

1. Try generating a component: `/mba-build-component component_name="button"`
2. Create a landing page: `/mba-build-landing-page product_name="Your Product"`
3. Build a dashboard: `/mba-build-dashboard-page dashboard_name="Your Dashboard"`
4. Explore the rules in `.cursor/rules/` to understand the system
5. Reference `.mba-template/` for design patterns

---

**Remember**: The goal is professional, human-quality designs. Every decision should be intentional and consistent.

