---
name: mba-build-design-system
description: Generate a complete design system with tokens, components, and documentation
---

# MBA Build Design System

Generate a comprehensive design system based on big tech patterns (Adobe Spectrum, IBM Carbon, Material Design 3, Apple HIG, Microsoft Fluent 2).

## Arguments

- `system_name` (required): Name of the design system (e.g., "Acme Design System")
- `theme` (optional): enterprise|neutral|editorial|playful - default: enterprise
- `base_unit` (optional): 2|4|8 - spacing base unit in pixels - default: 8
- `primary_color` (optional): Hex color for primary brand - default: #0078D4
- `platform` (optional): web|desktop|ios|android|cross-platform - default: web

## Instructions

1. **Review Reference Systems**:
   - Read `.mba-template/design-systems/` for patterns
   - Review `.cursor/rules/00-core-principles.mdc`
   - Check `.cursor/rules/30-color-system.mdc`
   - Check `.cursor/rules/40-spacing-layout.mdc`

2. **Generate Design Tokens** (`design-system/tokens.css`):
   - **Colors**: Primary, secondary, semantic (success, warning, error, info), neutrals (50-900)
   - **Spacing**: Based on base_unit (e.g., 8px: 8, 16, 24, 32, 40, 48, 64, 96)
   - **Typography**: Font families, sizes (12-64px), weights (400, 500, 600, 700), line heights
   - **Border Radius**: 4px, 8px, 12px, 16px
   - **Shadows**: 5 elevation levels
   - **Motion**: Duration (100ms, 200ms, 300ms, 500ms), easing curves

3. **Generate Foundation Styles**:
   - `design-system/reset.css`: Modern CSS reset
   - `design-system/typography.css`: Type scale and styles
   - `design-system/colors.css`: Color utilities
   - `design-system/spacing.css`: Spacing utilities
   - `design-system/elevation.css`: Shadow system
   - `design-system/motion.css`: Animation/transition utilities

4. **Generate Core Components**:
   - `design-system/components/button.css`: All button variants
   - `design-system/components/input.css`: Form inputs
   - `design-system/components/card.css`: Card component
   - `design-system/components/table.css`: Data table
   - `design-system/components/navigation.css`: Nav patterns
   - `design-system/components/modal.css`: Modal/dialog

5. **Theme Variants**:
   - **Enterprise**: Compact, subdued, data-dense
   - **Neutral**: Modern SaaS, balanced
   - **Editorial**: Spacious, typographic
   - **Playful**: Gradients, rounded, colorful

6. **Generate Documentation**:
   - `design-system/README.md`: Overview and usage
   - `design-system/docs/tokens.md`: Token documentation
   - `design-system/docs/components.md`: Component guide
   - `design-system/docs/patterns.md`: Design patterns
   - `design-system/examples/showcase.html`: Component showcase

7. **Platform Adaptations**:
   - Reference `.mba-template/platforms/{platform}.md`
   - Apply platform-specific patterns
   - Adjust sizing for platform (touch vs mouse)

## Output Structure

```
design-system/
├── tokens.css
├── reset.css
├── typography.css
├── colors.css
├── spacing.css
├── elevation.css
├── motion.css
├── components/
│   ├── button.css
│   ├── input.css
│   ├── card.css
│   ├── table.css
│   ├── navigation.css
│   └── modal.css
├── docs/
│   ├── tokens.md
│   ├── components.md
│   └── patterns.md
├── examples/
│   └── showcase.html
└── README.md
```

## Quality Checks

- [ ] All tokens defined with CSS variables
- [ ] Consistent spacing scale (no random values)
- [ ] WCAG AA color contrast
- [ ] Complete component set
- [ ] Documentation included
- [ ] Example showcase created
- [ ] Theme properly applied
- [ ] Platform-appropriate patterns

## Example Usage

```
/mba-build-design-system system_name="Acme Design System" theme="enterprise" base_unit="8" primary_color="#0066CC" platform="web"
```

This will generate an enterprise-themed design system with 8px spacing base and blue primary color for web platform.

