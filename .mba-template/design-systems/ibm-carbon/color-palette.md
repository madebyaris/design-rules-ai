# IBM Carbon - Color Palette

## Overview
Carbon uses a systematic color approach with specific roles and a 10-step scale for each color.

## Color Tokens

### Gray Scale (Neutral)
- **gray-10**: #f4f4f4 (lightest background)
- **gray-20**: #e0e0e0 (subtle background)
- **gray-30**: #c6c6c6 (disabled elements)
- **gray-40**: #a8a8a8 (placeholder text)
- **gray-50**: #8d8d8d (secondary icons)
- **gray-60**: #6f6f6f (secondary text)
- **gray-70**: #525252 (primary icons)
- **gray-80**: #393939 (primary text)
- **gray-90**: #262626 (high emphasis)
- **gray-100**: #161616 (maximum contrast)

### Blue (Primary/Interactive)
- **blue-10** through **blue-100**: Primary actions, links, focus states
- **blue-60**: Default interactive color (#0f62fe)
- **blue-70**: Hover state (#0353e9)

### Red (Danger/Error)
- **red-60**: Error states, destructive actions (#da1e28)
- **red-70**: Hover on destructive (#ba1b23)

### Green (Success)
- **green-60**: Success states, positive feedback (#24a148)

### Yellow (Warning)
- **yellow-30**: Warning backgrounds (#f1c21b)

## Themes

### White Theme (Light)
- Background: gray-10
- Surface: white (#ffffff)
- Text primary: gray-100
- Text secondary: gray-70
- Border: gray-30

### Gray 10 Theme
- Background: gray-10
- Surface: white
- Elevated surface: gray-10

### Gray 90 Theme (Dark)
- Background: gray-90
- Surface: gray-80
- Text primary: gray-10
- Text secondary: gray-30
- Border: gray-70

### Gray 100 Theme (High Contrast Dark)
- Background: gray-100
- Surface: gray-90
- Maximum contrast

## Layer System
Carbon uses layers for depth:
- **Layer 01**: Base layer (cards, panels)
- **Layer 02**: Elevated elements (dropdowns, tooltips)
- **Layer 03**: Highest elevation (modals, notifications)

## Accessibility
- All color combinations meet WCAG AA standards
- Text on background: minimum 4.5:1 contrast
- Large text (18px+): minimum 3:1 contrast
- Interactive elements: 3:1 contrast with surrounding colors

## Usage Guidelines
1. Use semantic tokens, not raw hex values
2. Maintain consistent color roles across themes
3. Test all themes for accessibility
4. Limit accent colors to 2-3 per interface

