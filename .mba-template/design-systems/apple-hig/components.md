# Apple HIG - Component Patterns

## Buttons (iOS)

### Styles
- **Filled**: High emphasis, tinted background
- **Gray**: Medium emphasis, gray background
- **Tinted**: Medium emphasis, tinted text
- **Plain**: Low emphasis, plain text

### Sizes
- **Small**: 28pt height
- **Medium**: 34pt height
- **Large**: 44pt height (default)

### Configurations
- **Title only**
- **Title + icon**
- **Icon only** (with label for accessibility)

## Navigation Bar

### Components
- **Title**: Centered or large (inline)
- **Back button**: Left side, automatic
- **Trailing buttons**: Right side (1-2 items)
- **Search bar**: Optional, below title

### Styles
- **Standard**: Translucent, adapts to scroll
- **Compact**: Smaller, for scrolled state
- **Large**: Large title, expands when at top

## Tab Bar

### Structure
- 2-5 tabs (3-4 recommended)
- Icon + label (both required)
- Badge (optional, for notifications)
- Selected state: Tinted icon + label

### Icon Size
- 25pt × 25pt (iPhone)
- 30pt × 30pt (iPad)
- Line weight: Regular or Medium

## Lists (Table View)

### Styles
- **Inset**: Rounded corners, margins
- **Inset Grouped**: Grouped sections
- **Plain**: Full width, no margins
- **Grouped**: Sections with headers

### Row Types
- **Default**: Title only
- **Subtitle**: Title + subtitle below
- **Value 1**: Title + value (right-aligned)
- **Value 2**: Title (left) + value (right)

### Accessories
- Disclosure indicator (chevron)
- Detail button (info icon)
- Checkmark
- Custom view

## Sheets & Modals

### Sheet (iOS 15+)
- **Medium detent**: Half screen
- **Large detent**: Full screen
- Drag indicator at top
- Dismiss by swiping down

### Modal
- Full screen or page sheet
- Close button (X) in nav bar
- Presented from bottom (iOS)

## Alerts & Action Sheets

### Alert
- Title (bold, 17pt)
- Message (regular, 13pt)
- 1-2 buttons (vertical if 2+)
- Destructive button (red text)

### Action Sheet
- Title (optional)
- Message (optional)
- Multiple actions (list)
- Cancel button (bottom, separated)

## Text Fields

### Styles
- **Rounded**: Rounded corners, fill background
- **Plain**: Underline only (macOS)

### Components
- Placeholder text
- Clear button (X)
- Left/right views (icons)
- Secure entry (password)

## Segmented Control

### Structure
- 2-5 segments
- Equal width or proportional
- Selected state: Filled
- Unselected: Transparent

### Usage
- Switching views/modes
- Filtering content
- Selecting options

## Progress Indicators

### Activity Indicator
- Spinning circle
- Small or large size
- Indeterminate progress

### Progress Bar
- Horizontal bar
- Determinate progress (0-100%)
- Track + fill

## Switches

### Structure
- Toggle control
- 51pt × 31pt
- On: Green (or accent color)
- Off: Gray

### Usage
- Binary on/off states
- Immediate effect
- Label on left

## Steppers

### Structure
- Minus button
- Value display
- Plus button
- Compact or expanded style

## Sliders

### Structure
- Track (gray)
- Fill (tinted)
- Thumb (circular)
- Min/max icons (optional)

## Pickers

### Styles
- **Wheel**: Spinning wheel (iOS)
- **Menu**: Dropdown menu
- **Inline**: Expanded list
- **Compact**: Button that opens menu

### Date Picker
- Wheel style (iOS)
- Graphical style (calendar)
- Compact style (button)

## Context Menus

### Structure
- Triggered by long press
- List of actions
- Icons + labels
- Destructive action (red, bottom)
- Preview (optional)

## Toolbars

### iOS Toolbar
- Height: 44pt
- Bottom of screen
- 2-5 items
- Equal spacing

### macOS Toolbar
- Height: 52pt
- Top of window
- Customizable items
- Icon + label or icon only

