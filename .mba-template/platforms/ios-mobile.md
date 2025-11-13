# iOS Mobile Design Guidelines

## Safe Area & Layout

### Safe Area Insets
- **Top**: Status bar + notch/Dynamic Island (44-59pt)
- **Bottom**: Home indicator area (34pt)
- **Sides**: 0pt (portrait), varies (landscape)

### Screen Sizes (Points)
- **iPhone SE**: 375 × 667
- **iPhone 13/14**: 390 × 844
- **iPhone 13/14 Pro**: 393 × 852
- **iPhone 13/14 Plus**: 428 × 926
- **iPhone 13/14 Pro Max**: 430 × 932

### Layout Margins
- **Standard**: 16pt (iPhone), 20pt (iPad)
- **Readable Content**: 672pt maximum width

## Navigation Patterns

### Navigation Bar
- **Height**: 44pt (compact), 96pt (large title)
- **Large Title**: 34pt, bold
- **Standard Title**: 17pt, semibold
- **Back Button**: Automatic, with previous screen title
- **Trailing Buttons**: 1-2 items maximum

### Tab Bar
- **Height**: 49pt (iPhone), 50pt (iPad)
- **Items**: 2-5 tabs (3-4 recommended)
- **Icon Size**: 25pt × 25pt (iPhone), 30pt × 30pt (iPad)
- **Label**: 10pt
- **Badge**: Red dot for notifications

### Toolbar
- **Height**: 44pt
- **Position**: Bottom of screen
- **Items**: 2-5 buttons
- **Spacing**: Equal distribution

## Touch Targets

### Minimum Sizes
- **Touch target**: 44pt × 44pt minimum
- **Recommended**: 48pt × 48pt
- **Spacing**: 8pt minimum between targets

### Gestures
- **Tap**: Primary action
- **Long press**: Context menu
- **Swipe**: Navigate back, delete, reveal actions
- **Pinch**: Zoom
- **Drag**: Reorder, move

## Typography

### Text Styles (Dynamic Type)
- **Large Title**: 34pt
- **Title 1**: 28pt
- **Title 2**: 22pt
- **Title 3**: 20pt
- **Headline**: 17pt, semibold
- **Body**: 17pt
- **Callout**: 16pt
- **Subheadline**: 15pt
- **Footnote**: 13pt
- **Caption 1**: 12pt
- **Caption 2**: 11pt

### Font
- **SF Pro**: System font
- **SF Pro Rounded**: Rounded variant
- **New York**: Serif (optional)
- **SF Mono**: Monospace

### Dynamic Type
- Support all 12 text sizes
- Test with largest accessibility sizes
- Never use fixed font sizes

## Colors

### System Colors
- **Blue**: #007AFF (links, primary actions)
- **Green**: #34C759 (success)
- **Red**: #FF3B30 (destructive, errors)
- **Orange**: #FF9500 (warnings)
- **Gray**: #8E8E93 (secondary elements)

### Semantic Colors
- **Label**: Primary text
- **Secondary Label**: Secondary text
- **Tertiary Label**: Placeholder text
- **System Background**: Primary background
- **Secondary System Background**: Grouped backgrounds

### Dark Mode
- All colors adapt automatically
- Use semantic color names
- Test in both light and dark modes

## Components

### Buttons
- **Filled**: High emphasis, tinted background
- **Gray**: Medium emphasis
- **Tinted**: Medium emphasis, tinted text
- **Plain**: Low emphasis
- **Sizes**: Small (28pt), Medium (34pt), Large (44pt)

### Lists (Table View)
- **Row Height**: 44pt (default), 56pt (subtitle)
- **Inset**: 16pt margins, rounded corners
- **Grouped**: Sections with headers
- **Swipe Actions**: Leading and trailing
- **Accessories**: Disclosure, detail, checkmark

### Sheets
- **Medium Detent**: Half screen
- **Large Detent**: Full screen
- **Drag Indicator**: 5pt × 36pt
- **Dismiss**: Swipe down

### Alerts
- **Title**: 17pt, semibold
- **Message**: 13pt
- **Buttons**: 1-2 (horizontal), 2+ (vertical)
- **Destructive**: Red text

### Action Sheets
- **Actions**: List of options
- **Cancel**: Bottom, separated
- **Destructive**: Red text
- **Dismiss**: Tap outside or Cancel

## Layout Patterns

### List-Detail
- **iPhone**: Navigation stack
- **iPad**: Split view (list | detail)
- **Compact**: Full-screen views
- **Regular**: Side-by-side

### Tab-Based
- **Tab Bar**: Bottom navigation
- **3-5 Tabs**: Primary sections
- **More**: Overflow tab if needed
- **Badge**: Notifications indicator

### Modal
- **Full Screen**: Complete takeover
- **Page Sheet**: Card from bottom
- **Form Sheet**: Centered (iPad)
- **Dismiss**: Swipe down or button

## Interaction

### Haptic Feedback
- **Light**: Selection change
- **Medium**: Action confirmation
- **Heavy**: Error, warning
- **Success**: Task completion
- **Warning**: Caution
- **Error**: Failure

### Animations
- **Duration**: 0.2-0.3s (quick), 0.3-0.5s (standard)
- **Easing**: Ease-in-out (default)
- **Spring**: Natural, bouncy
- **Reduce Motion**: Respect user preference

### Loading States
- **Activity Indicator**: Indeterminate
- **Progress Bar**: Determinate
- **Pull to Refresh**: Standard gesture
- **Skeleton Screens**: Content placeholders

## Keyboard

### Input Types
- **default**: Standard keyboard
- **email**: @ and . keys
- **number**: Numeric keypad
- **phone**: Phone number pad
- **url**: .com and / keys
- **search**: Search button

### Keyboard Toolbar
- **Done/Next/Go**: Action button
- **Prev/Next**: Navigate fields
- **Dismiss**: Close keyboard

### Keyboard Avoidance
- Scroll content above keyboard
- Resize input area
- Maintain focus visibility

## Status Bar

### Styles
- **Default**: Dark content (light background)
- **Light Content**: Light content (dark background)
- **Dark Content**: Dark content (always)

### Content
- **Time**: Left side
- **Notch/Island**: Center
- **Battery/Signal**: Right side

## Accessibility

### VoiceOver
- All elements labeled
- Meaningful descriptions
- Logical reading order
- Custom actions for complex controls

### Dynamic Type
- Support all 12 sizes
- Layout adapts to text size
- No truncation at large sizes

### Reduce Motion
- Disable animations
- Fade instead of slide
- Respect user preference

### Contrast
- WCAG AA minimum (4.5:1)
- Test in both light and dark modes
- High contrast mode support

## Best Practices

### Do:
- Use system components
- Support Dynamic Type
- Respect safe areas
- Test on multiple devices
- Support dark mode
- Use SF Symbols
- Follow HIG guidelines
- Test with VoiceOver
- Support landscape (if appropriate)
- Use haptic feedback appropriately

### Don't:
- Ignore safe areas
- Use fixed font sizes
- Block gestures (swipe back)
- Use custom UI unnecessarily
- Ignore dark mode
- Use non-standard patterns
- Require precise taps
- Ignore accessibility
- Force orientation
- Overuse haptics

