# Microsoft Fluent 2 - Color System

## Color Ramps
Fluent 2 uses color ramps with 16 shades (0-160) for each color.

### Neutral Colors
- **Gray 0-160**: From white to black
- **Gray 14**: Default background (light mode)
- **Gray 160**: Default background (dark mode)
- **Gray 130**: Primary text (light mode)
- **Gray 24**: Primary text (dark mode)

### Brand/Accent Colors
Each brand color has a full ramp (0-160):
- **Blue**: Default accent (#0078D4)
- **Red**: Error, destructive
- **Green**: Success
- **Yellow**: Warning
- **Purple, Teal, Orange**: Alternative accents

## Semantic Tokens

### Backgrounds
- **Canvas**: Page background
- **Layer**: Surface background (cards, panels)
- **Layer Alt**: Alternative surface
- **Overlay**: Modal/dialog overlay

### Text
- **Text Primary**: High emphasis text
- **Text Secondary**: Medium emphasis
- **Text Tertiary**: Low emphasis
- **Text Disabled**: Disabled state

### Borders
- **Stroke 1**: Subtle borders (1px)
- **Stroke 2**: Standard borders
- **Stroke Accessible**: High contrast borders

### States
- **Hover**: Subtle background change
- **Pressed**: Darker background
- **Selected**: Accent color tint
- **Focus**: 2px accent outline

## Shared Colors
Cross-platform semantic colors:
- **Brand Background**: Primary brand color
- **Danger Background**: Error/destructive
- **Success Background**: Success/positive
- **Warning Background**: Warning/caution

## Accessibility
- All combinations meet WCAG AA (4.5:1)
- High contrast mode support
- Forced colors mode support (Windows)
- Never rely on color alone

## Themes

### Light Mode
- Background: Gray 14
- Surface: White (Gray 0)
- Text: Gray 130
- Border: Gray 30

### Dark Mode
- Background: Gray 160
- Surface: Gray 150
- Text: Gray 24
- Border: Gray 130

### High Contrast
- Forced colors from OS
- Semantic tokens map to system colors
- Borders always visible

