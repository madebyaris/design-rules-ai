# IBM Carbon - Component Patterns

## Button

### Variants
- **Primary**: Filled, high emphasis, blue background
- **Secondary**: Outlined, medium emphasis
- **Tertiary**: Ghost, low emphasis, no border
- **Danger**: Red, for destructive actions
- **Danger--tertiary**: Red text, ghost style

### Sizes
- **Small**: 32px height
- **Medium**: 40px height (default)
- **Large**: 48px height
- **Extra Large**: 64px height
- **2X Large**: 80px height

### Structure
- Icon (optional, 16px)
- Label (required)
- Padding: 16px horizontal, calculated vertical

### States
- Default, Hover, Active, Focus, Disabled
- Focus: 2px blue inset border

## Text Input

### Structure
- Label (required, 12px)
- Input field (40px height default)
- Helper text (optional, 12px)
- Error/warning message (12px)

### Variants
- Default
- Fluid (full width)
- With icon
- Password (with show/hide toggle)

### States
- Default, Focus, Error, Warning, Disabled, Read-only

## Dropdown/Select

### Structure
- Label (12px)
- Selected value display (40px height)
- Dropdown icon (16px chevron)
- Menu (overlay, max 10 items visible)

### States
- Closed, Open, Focus, Error, Disabled

## Checkbox & Radio

### Sizes
- Small: 16px
- Medium: 20px (default)

### Structure
- Input indicator
- Label text (14px)
- Helper text (optional, 12px)

### States
- Unchecked, Checked, Indeterminate (checkbox only), Focus, Disabled

## Data Table

### Structure
- Header row (background: gray-20)
- Body rows (alternating optional)
- Sortable columns (with icon)
- Batch actions toolbar
- Pagination

### Row Heights
- **Compact**: 24px
- **Short**: 32px
- **Normal**: 48px (default)
- **Tall**: 64px

### Cell Padding
- Horizontal: 16px
- Vertical: varies by row height

### Features
- Sortable columns
- Selectable rows (checkbox)
- Expandable rows
- Inline editing
- Batch actions
- Search/filter

## Modal

### Sizes
- **Extra Small**: 384px
- **Small**: 512px
- **Medium**: 768px (default)
- **Large**: 1024px

### Structure
- Overlay (gray-100 at 50% opacity)
- Container (centered)
- Header (label + title + close button)
- Body (scrollable content)
- Footer (actions, right-aligned)

### Padding
- All sides: 16px (small) or 24px (medium+)

## Notification/Toast

### Variants
- **Inline**: Within page flow
- **Toast**: Floating, auto-dismiss
- **Banner**: Full-width, persistent

### Types
- Info (blue)
- Success (green)
- Warning (yellow)
- Error (red)

### Structure
- Icon (16px)
- Title (14px, semi-bold)
- Subtitle (14px)
- Action button (optional)
- Close button

## Tabs

### Variants
- **Default**: Horizontal, underline indicator
- **Container**: With background
- **Contained**: Tabs within a container

### Structure
- Tab item (40px height)
- Label (14px)
- Active indicator (2px blue underline)
- Content panel

### States
- Default, Hover, Active, Focus, Disabled

## Accordion

### Structure
- Header (40-48px height)
- Title (14px)
- Chevron icon (16px)
- Content panel (collapsible)

### States
- Collapsed, Expanded, Focus, Disabled

## Tag

### Sizes
- **Small**: 18px height
- **Medium**: 24px height (default)

### Variants
- **Read-only**: Display only
- **Dismissible**: With close button
- **Selectable**: Interactive, can be toggled
- **Operational**: With icon

### Colors
- Red, Magenta, Purple, Blue, Cyan, Teal, Green, Gray, Cool-gray, Warm-gray

## Breadcrumb

### Structure
- Items separated by slash (/)
- Current page (no link, gray-70)
- Previous pages (links, blue-60)
- Overflow menu for long paths

### Sizes
- Default: 14px
- Large: 16px

## Pagination

### Structure
- Items per page selector
- Page number display
- Previous/Next buttons
- First/Last buttons (optional)

### Variants
- **Default**: Full controls
- **Simple**: Just prev/next

