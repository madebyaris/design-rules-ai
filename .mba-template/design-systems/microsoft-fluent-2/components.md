# Microsoft Fluent 2 - Component Patterns

## Button

### Variants
- **Primary**: Filled, high emphasis, brand color
- **Outline**: Outlined, medium emphasis
- **Subtle**: Ghost, low emphasis
- **Transparent**: No background, minimal emphasis

### Sizes
- **Small**: 24px height
- **Medium**: 32px height (default)
- **Large**: 40px height

### Structure
- Icon (optional, 16px or 20px)
- Label (required)
- Padding: 12px horizontal (medium)

### States
- Default, Hover, Pressed, Disabled, Focus (2px outline)

## Input

### Variants
- **Outline**: With border (default)
- **Underline**: Underline only
- **Filled**: With background

### Structure
- Label (above or floating)
- Input field (32px height)
- Content before/after (icons)
- Description text (below)
- Error message (below, red)

### States
- Default, Hover, Focus, Error, Disabled, Read-only

## Dropdown/Combobox

### Structure
- Label (optional)
- Selected value display
- Chevron icon (12px)
- Dropdown menu (overlay)
- Search (optional, in menu)

### Menu
- Max height: 300px (scrollable)
- Item height: 32px
- Item padding: 8px horizontal

## Checkbox & Radio

### Sizes
- Small: 16px
- Medium: 20px (default)
- Large: 24px

### Structure
- Input indicator
- Label (right of indicator)
- Description (optional, below)

### States
- Unchecked, Checked, Indeterminate, Disabled

## Card

### Variants
- **Filled**: With background
- **Outline**: With border
- **Subtle**: Minimal styling

### Structure
- Header (optional)
- Preview (optional, image/media)
- Content area
- Footer (optional, actions)

### Interaction
- Static (non-interactive)
- Selectable (checkbox)
- Navigable (clickable)

## Dialog/Modal

### Sizes
- Small: 480px
- Medium: 600px (default)
- Large: 840px

### Structure
- Overlay (backdrop)
- Surface (dialog container)
- Title (20px, semibold)
- Content (scrollable)
- Actions (footer, right-aligned)

### Types
- **Modal**: Blocks interaction
- **Non-modal**: Allows background interaction
- **Alert**: Simple message + actions

## Tabs

### Variants
- **Horizontal**: Default, top of content
- **Vertical**: Side of content

### Structure
- Tab item (32px height)
- Label (14px)
- Icon (optional, 20px)
- Active indicator (2px underline or background)

### States
- Default, Hover, Selected, Disabled

## Menu

### Structure
- Menu item (32px height)
- Icon (optional, left, 20px)
- Label (14px)
- Shortcut (optional, right)
- Submenu indicator (chevron)

### Dividers
- 1px line between groups
- 8px spacing around divider

### Types
- **Context menu**: Right-click
- **Dropdown menu**: From button
- **Menu bar**: Top of window

## Accordion

### Structure
- Header (44px height)
- Title (14px, semibold)
- Chevron icon (12px, rotates)
- Content panel (collapsible)
- Padding: 12px

### States
- Collapsed, Expanded, Hover, Focus

## Tooltip

### Structure
- Arrow pointing to target
- Content (max 200px width)
- Padding: 8px 12px
- Text: 12px

### Positioning
- Above (preferred)
- Below, Left, Right (fallback)
- Auto-adjust to viewport

## Badge

### Sizes
- Tiny: 6px (dot only)
- Small: 16px
- Medium: 20px (default)
- Large: 24px

### Variants
- **Filled**: Solid background
- **Ghost**: Outlined
- **Tint**: Subtle background

### Usage
- Notification count
- Status indicator
- Category label

## Progress

### Variants
- **Bar**: Horizontal bar
- **Ring**: Circular progress
- **Spinner**: Indeterminate loading

### Bar
- Height: 2px (thin), 4px (default), 8px (thick)
- Indeterminate: Animated gradient

### Ring
- Sizes: 16px, 20px, 24px, 28px, 32px
- Stroke width: 2px, 3px, 4px

## Avatar

### Sizes
- 20px, 24px, 28px, 32px, 36px, 40px, 48px, 56px, 64px, 72px, 96px, 120px, 128px

### Variants
- **Image**: User photo
- **Icon**: Generic icon
- **Initials**: User initials (1-2 letters)

### Badge
- Status indicator (online, busy, away, offline)
- Position: Bottom-right corner

## Divider

### Variants
- **Default**: Horizontal line
- **Vertical**: Vertical line
- **Subtle**: Lighter color
- **Strong**: Darker color
- **With content**: Text or icon in center

### Thickness
- 1px (default)
- 2px (strong)

## Persona/Profile Card

### Structure
- Avatar (48px or larger)
- Primary text (name, 14px semibold)
- Secondary text (role, 12px)
- Tertiary text (optional, 12px)
- Presence badge (status)

### Sizes
- Small: Compact layout
- Large: Extended info, actions

