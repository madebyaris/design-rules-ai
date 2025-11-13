# Adobe Spectrum - Component Patterns

## Button

### Variants
- **Primary (CTA)**: Filled, high emphasis, blue background
- **Secondary**: Outlined, medium emphasis, transparent background
- **Negative**: Red, for destructive actions
- **Quiet**: Text-only, low emphasis

### Sizes
- **Small**: 24px height, 8px 12px padding
- **Medium**: 32px height, 12px 16px padding
- **Large**: 40px height, 16px 24px padding
- **Extra Large**: 48px height, 20px 32px padding

### States
- Default, Hover, Active, Focus, Disabled
- Focus: 2px blue outline, 2px offset

## Input Fields

### Variants
- **Text Input**: Single line
- **Text Area**: Multi-line
- **Search**: With search icon
- **Number**: With increment/decrement

### Structure
- Label (12-14px, above input)
- Input field (32-40px height)
- Help text (12px, below input)
- Error text (12px, red, below input)

### States
- Default, Hover, Focus, Error, Disabled, Read-only

## Card

### Structure
- Container with subtle border or elevation
- Optional header (title + actions)
- Content area (flexible)
- Optional footer (actions)

### Spacing
- Padding: 16-24px
- Gap between elements: 12-16px

### Variants
- **Flat**: Border only, no shadow
- **Elevated**: Subtle shadow
- **Interactive**: Hover state, clickable

## Table

### Structure
- Header row (bold, background color)
- Body rows (alternating background optional)
- Sortable columns (with icon)
- Pagination controls

### Spacing
- Cell padding: 8px 12px
- Row height: 40-48px
- Column gap: 16px

### States
- Row hover: subtle background
- Selected row: blue tint
- Sortable header: pointer cursor

## Navigation

### Top Navigation
- Height: 48-56px
- Logo/brand on left
- Primary nav items center or right
- User menu on far right

### Side Navigation
- Width: 240-280px (expanded), 56px (collapsed)
- Nav items: 40px height, 12px 16px padding
- Active state: blue background or left border
- Collapsible sections

### Bottom Tab Bar (Mobile)
- Height: 56px
- 3-5 items
- Icon + label
- Active state: blue color

## Modal/Dialog

### Structure
- Overlay (semi-transparent black)
- Dialog container (centered, max-width 600px)
- Header (title + close button)
- Content area (scrollable if needed)
- Footer (action buttons)

### Spacing
- Padding: 24-32px
- Button gap: 8px
- Title to content: 16px

## Form Layout

### Structure
- Label above field (12-14px)
- Field (32-40px height)
- Help text below (12px)
- Vertical spacing: 16-24px between fields
- Group related fields with visual separation

### Validation
- Inline validation on blur
- Error message below field
- Error icon in field
- Red border on error state

