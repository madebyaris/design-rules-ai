# Android Mobile Design Guidelines

## Material Design 3 Principles

### Dynamic Color
- Colors extracted from wallpaper
- Tonal palettes (13 tones per color)
- Semantic color roles
- Light and dark themes

### Elevation & Shadows
- Surface tinting instead of shadows
- 5 elevation levels (0-5)
- Higher elevation = more tint

## Screen Sizes & Density

### Breakpoints (dp)
- **Compact**: 0-599dp (phone portrait)
- **Medium**: 600-839dp (tablet, phone landscape)
- **Expanded**: 840dp+ (tablet, desktop)

### Density Buckets
- **ldpi**: 120 dpi (~0.75x)
- **mdpi**: 160 dpi (1x baseline)
- **hdpi**: 240 dpi (~1.5x)
- **xhdpi**: 320 dpi (2x)
- **xxhdpi**: 480 dpi (3x)
- **xxxhdpi**: 640 dpi (4x)

### Common Resolutions
- **Phone**: 360 × 640dp, 360 × 800dp, 412 × 915dp
- **Tablet**: 600 × 960dp, 768 × 1024dp

## Navigation Patterns

### Top App Bar
- **Height**: 64dp (default), 128dp (large)
- **Title**: 22px (Title Large)
- **Icons**: 24dp
- **Elevation**: Level 0 (scrolled: Level 2)

### Bottom Navigation Bar
- **Height**: 80dp
- **Items**: 3-5 destinations
- **Icon**: 24dp
- **Label**: 12px (Label Medium)
- **Active Indicator**: Pill shape

### Navigation Drawer
- **Width**: 360dp (standard), 256dp (modal)
- **Header**: Optional
- **Items**: Icon + label
- **Active Indicator**: Pill shape
- **Elevation**: Level 1 (modal: Level 3)

### Navigation Rail
- **Width**: 80dp
- **Vertical**: Side of screen
- **Icon**: 24dp
- **Label**: Optional
- **FAB**: Optional at top

## Touch Targets

### Minimum Sizes
- **Touch target**: 48dp × 48dp minimum
- **Icon button**: 48dp × 48dp
- **Spacing**: 8dp minimum between targets

### Gestures
- **Tap**: Primary action
- **Long press**: Context menu, drag
- **Swipe**: Dismiss, navigate, reveal actions
- **Pinch**: Zoom
- **Drag**: Reorder, scroll

## Typography

### Roboto Font
- **Default**: Roboto, system-ui, sans-serif
- **Weights**: 400 (Regular), 500 (Medium)

### Type Scale
- **Display Large**: 57px / 64px line-height
- **Display Medium**: 45px / 52px
- **Display Small**: 36px / 44px
- **Headline Large**: 32px / 40px
- **Headline Medium**: 28px / 36px
- **Headline Small**: 24px / 32px
- **Title Large**: 22px / 28px
- **Title Medium**: 16px / 24px, weight 500
- **Title Small**: 14px / 20px, weight 500
- **Body Large**: 16px / 24px
- **Body Medium**: 14px / 20px
- **Body Small**: 12px / 16px
- **Label Large**: 14px / 20px, weight 500
- **Label Medium**: 12px / 16px, weight 500
- **Label Small**: 11px / 16px, weight 500

## Colors

### Color Roles
- **Primary**: Main brand color
- **On Primary**: Text/icons on primary
- **Primary Container**: Less prominent primary
- **On Primary Container**: Text on container
- **Secondary, Tertiary**: Similar pattern
- **Error**: Error states
- **Surface**: Component backgrounds
- **Outline**: Borders

### Elevation Tint
- Level 0: No tint
- Level 1: 5% primary tint
- Level 2: 8% primary tint
- Level 3: 11% primary tint
- Level 4: 12% primary tint
- Level 5: 14% primary tint

## Components

### Buttons
- **Filled**: High emphasis, 40dp height
- **Filled Tonal**: Medium emphasis
- **Outlined**: Medium emphasis
- **Text**: Low emphasis
- **Elevated**: Medium emphasis with shadow
- **Padding**: 24dp horizontal
- **Icon**: 18dp

### FAB (Floating Action Button)
- **Small**: 40dp
- **Medium**: 56dp (default)
- **Large**: 96dp
- **Extended**: Variable width, 56dp height
- **Elevation**: Level 3 (pressed: Level 4)

### Cards
- **Elevated**: Shadow, Level 1
- **Filled**: Tinted background
- **Outlined**: Border, no shadow
- **Padding**: 16dp

### Text Fields
- **Filled**: Background fill, 56dp height
- **Outlined**: Border, 56dp height
- **Label**: Floating or fixed
- **Icons**: Leading/trailing, 24dp
- **Helper Text**: 12px below
- **Error Text**: 12px below, error color

### Chips
- **Assist**: Suggestions
- **Filter**: Toggle selection
- **Input**: User-entered
- **Suggestion**: Recommendations
- **Height**: 32dp
- **Padding**: 16dp horizontal
- **Icon**: 18dp

### Dialogs
- **Basic**: Simple message + actions
- **Full-screen**: Mobile, full screen
- **Width**: 280-560dp
- **Padding**: 24dp
- **Actions**: Right-aligned

### Snackbar
- **Height**: 48-68dp
- **Width**: 344-672dp (desktop), full-width (mobile)
- **Text**: 14px
- **Action**: Optional button
- **Duration**: 4-10 seconds
- **Position**: Bottom center

### Lists
- **One-line**: 56dp height
- **Two-line**: 72dp height
- **Three-line**: 88dp height
- **Padding**: 16dp horizontal
- **Icon**: 24dp, 40dp from left
- **Avatar**: 40dp

## Layout

### Spacing (4dp base)
- **4dp**: Minimal
- **8dp**: Standard unit
- **12dp**: Small
- **16dp**: Medium
- **24dp**: Large
- **32dp**: Extra large
- **48dp**: Section spacing

### Grid
- **Columns**: 4 (mobile), 8 (tablet), 12 (desktop)
- **Gutters**: 16dp (mobile), 24dp (tablet/desktop)
- **Margins**: 16dp (mobile), 24dp (tablet/desktop)

## System UI

### Status Bar
- **Height**: 24dp
- **Icons**: White (dark theme), dark (light theme)
- **Translucent**: Optional

### Navigation Bar (System)
- **Height**: 48dp (3-button), 24dp (gesture)
- **Buttons**: Back, Home, Recents
- **Gesture**: Swipe up for home

## Interaction

### Ripple Effect
- Touch feedback on interactive elements
- Circular expansion from touch point
- Color: Primary color at 12-16% opacity
- Duration: 300-450ms

### State Layers
- **Hover**: 8% opacity
- **Focus**: 12% opacity
- **Pressed**: 12% opacity
- **Dragged**: 16% opacity

### Motion
- **Duration Fast**: 100ms
- **Duration Medium**: 300ms
- **Duration Slow**: 500ms
- **Easing**: Standard, emphasized, decelerate

## Accessibility

### TalkBack (Screen Reader)
- Content descriptions for all elements
- Meaningful labels
- Logical reading order
- Custom actions for complex controls

### Large Text
- Support system font scaling
- Test at 200% scale
- No truncation at large sizes
- Layout adapts to text size

### Touch Target Size
- Minimum 48dp × 48dp
- Adequate spacing between targets
- Visual feedback on touch

### Color Contrast
- WCAG AA minimum (4.5:1)
- Test in light and dark themes
- Color not sole indicator

## Best Practices

### Do:
- Use Material Components
- Support dynamic color
- Respect system theme
- Support gesture navigation
- Use semantic color roles
- Follow Material guidelines
- Test on multiple devices
- Support TalkBack
- Handle configuration changes
- Use vector drawables (SVG)

### Don't:
- Ignore Material guidelines
- Use fixed colors (use tokens)
- Block system gestures
- Use custom UI unnecessarily
- Ignore dark theme
- Use non-standard patterns
- Require precise touches
- Ignore accessibility
- Hardcode dimensions
- Use bitmap icons at multiple densities

