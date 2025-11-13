# Apple HIG - Color Palette

## System Colors (iOS/iPadOS)

### Dynamic Colors (adapt to light/dark mode)
- **Label**: Primary text
- **Secondary Label**: Secondary text
- **Tertiary Label**: Tertiary text, placeholder
- **Quaternary Label**: Watermark text

### Background Colors
- **System Background**: Primary background
- **Secondary System Background**: Grouped content background
- **Tertiary System Background**: Grouped content within grouped content

### Fill Colors (for UI elements)
- **System Fill**: Thin materials, backgrounds
- **Secondary System Fill**: Medium materials
- **Tertiary System Fill**: Thick materials
- **Quaternary System Fill**: Extra thick materials

### Semantic Colors
- **System Blue**: Links, selected state (#007AFF light, #0A84FF dark)
- **System Green**: Success, positive (#34C759 light, #30D158 dark)
- **System Indigo**: Alternative accent (#5856D6 light, #5E5CE6 dark)
- **System Orange**: Warning (#FF9500 light, #FF9F0A dark)
- **System Pink**: Creative, playful (#FF2D55 light, #FF375F dark)
- **System Purple**: Creative (#AF52DE light, #BF5AF2 dark)
- **System Red**: Destructive, error (#FF3B30 light, #FF453A dark)
- **System Teal**: Alternative accent (#5AC8FA light, #64D2FF dark)
- **System Yellow**: Warning (#FFCC00 light, #FFD60A dark)

### Gray Scale
- **System Gray**: #8E8E93 (light), #8E8E93 (dark)
- **System Gray 2-6**: Progressively lighter/darker

## macOS Colors

### Accent Colors
- Blue (default), Purple, Pink, Red, Orange, Yellow, Green, Graphite

### Control Colors
- **Control Accent Color**: User's chosen accent
- **Control Background Color**: Button, slider backgrounds
- **Selected Content Background Color**: Selected items

## Usage Guidelines
1. Use semantic colors for their intended purpose
2. Never hardcode RGB values; use system colors
3. Test in both light and dark modes
4. Respect user's accent color preference
5. Maintain 4.5:1 contrast for text

## Vibrancy
iOS uses vibrancy effects that adapt to background:
- Light vibrancy on dark backgrounds
- Dark vibrancy on light backgrounds
- Ultra-thin, thin, regular, thick materials

