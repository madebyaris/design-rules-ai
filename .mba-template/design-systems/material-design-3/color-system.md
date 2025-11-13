# Material Design 3 - Color System

## Overview
Material Design 3 introduces dynamic color with tonal palettes and semantic roles.

## Color Roles

### Primary
- **Primary**: Main brand color, primary actions
- **On-Primary**: Text/icons on primary
- **Primary Container**: Less prominent primary elements
- **On-Primary Container**: Text on primary container

### Secondary
- **Secondary**: Complementary color, secondary actions
- **On-Secondary**: Text/icons on secondary
- **Secondary Container**: Less prominent secondary elements
- **On-Secondary Container**: Text on secondary container

### Tertiary
- **Tertiary**: Contrasting accent color
- **On-Tertiary**: Text/icons on tertiary
- **Tertiary Container**: Less prominent tertiary elements
- **On-Tertiary Container**: Text on tertiary container

### Error
- **Error**: Error states, destructive actions
- **On-Error**: Text/icons on error
- **Error Container**: Error backgrounds
- **On-Error Container**: Text on error container

### Neutral/Surface
- **Surface**: Component backgrounds
- **On-Surface**: Text/icons on surface
- **Surface Variant**: Alternative surface color
- **On-Surface Variant**: Text on surface variant
- **Outline**: Borders, dividers
- **Outline Variant**: Subtle borders

### Background
- **Background**: App background
- **On-Background**: Text/icons on background

## Tonal Palettes
Each color has 13 tones (0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 95, 99, 100):
- 0: Black
- 10-30: Dark tones
- 40-60: Mid tones
- 70-90: Light tones
- 95-99: Very light tones
- 100: White

## Dynamic Color
Material You generates color schemes from:
- User wallpaper
- Custom seed color
- System preferences (light/dark)

## Elevation & Tint
Surfaces at higher elevations receive a tint of the primary color:
- Level 0: No tint
- Level 1: 5% primary tint
- Level 2: 8% primary tint
- Level 3: 11% primary tint
- Level 4: 12% primary tint
- Level 5: 14% primary tint

## Accessibility
- All color combinations meet WCAG AA (4.5:1 for text)
- High contrast mode available
- Color is never the only indicator

