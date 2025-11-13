# Desktop App Design Guidelines (Electron/Tauri)

## Platform Considerations

### Window Management
- **Title bar**: Native or custom frameless
- **Window controls**: Close, minimize, maximize/restore
- **Drag region**: Top area for moving window
- **Resize**: All edges and corners
- **Multiple windows**: Support if needed

### Menu Bar
- **File**: New, Open, Save, Close, Exit
- **Edit**: Undo, Redo, Cut, Copy, Paste
- **View**: Zoom, Full Screen, Toggle Sidebar
- **Window**: Minimize, Zoom, Bring All to Front
- **Help**: Documentation, About

### Keyboard Shortcuts
- **Cmd/Ctrl + N**: New
- **Cmd/Ctrl + O**: Open
- **Cmd/Ctrl + S**: Save
- **Cmd/Ctrl + W**: Close window
- **Cmd/Ctrl + Q**: Quit app
- **Cmd/Ctrl + ,**: Preferences
- **Cmd/Ctrl + F**: Find
- **Cmd/Ctrl + Z**: Undo
- **Cmd/Ctrl + Shift + Z**: Redo

## Layout Patterns

### Application Shell
- **Title bar**: 32-40px height (Windows), 22px (macOS)
- **Menu bar**: 28-32px height
- **Toolbar**: 40-48px height
- **Sidebar**: 200-280px width (collapsible)
- **Main content**: Flexible
- **Status bar**: 24-28px height (optional)

### Sidebar Navigation
- Width: 240-280px (expanded), 48-56px (collapsed)
- Item height: 32-40px
- Icon size: 20-24px
- Padding: 8-12px
- Active indicator: Background or left border

### Toolbar
- Height: 40-48px
- Icon buttons: 32-36px
- Spacing: 4-8px between items
- Groups: Separated by dividers
- Tooltips: On hover (500ms delay)

## Interaction Patterns

### Mouse Interaction
- **Click targets**: Minimum 24px × 24px
- **Hover states**: Essential for all interactive elements
- **Right-click**: Context menus
- **Double-click**: Open/activate
- **Drag & drop**: For file operations, reordering

### Keyboard Navigation
- **Tab**: Navigate between controls
- **Shift + Tab**: Navigate backwards
- **Enter/Space**: Activate button/checkbox
- **Arrow keys**: Navigate lists, menus
- **Escape**: Close dialogs, cancel actions
- **Cmd/Ctrl + Tab**: Switch between tabs/views

### Focus Management
- Visible focus indicators (2px outline)
- Logical tab order
- Focus trap in modals
- Return focus after dialog close

## Platform-Specific Patterns

### Windows
- **Title bar**: 32px height, window controls right
- **Menu bar**: Integrated or separate
- **Accent color**: System accent color
- **Shadows**: Prominent window shadows
- **Corners**: Slightly rounded (Windows 11)

### macOS
- **Title bar**: 22px height, traffic lights left
- **Menu bar**: System menu bar (top of screen)
- **Vibrancy**: Translucent effects
- **Shadows**: Subtle window shadows
- **Corners**: Rounded corners

### Linux
- **Title bar**: Varies by DE (32-40px)
- **Menu bar**: Application or global
- **Theme**: Respect system theme
- **Shadows**: Varies by compositor

## System Integration

### System Tray/Menu Bar Icon
- Icon size: 16px × 16px (Windows), 22px × 22px (macOS)
- Monochrome icon (adapts to theme)
- Context menu on right-click
- Notifications badge

### Notifications
- Native system notifications
- Title + body text
- Optional icon
- Actions (buttons)
- Sound (optional, respect system settings)

### File System
- Native file picker dialogs
- Drag & drop files into app
- Recent files list
- Auto-save and recovery

### System Preferences
- Respect system theme (light/dark)
- Respect reduced motion
- Respect high contrast
- System font scaling

## Performance

### Startup Time
- Fast launch (< 2 seconds)
- Splash screen if needed
- Progressive loading
- Remember window state

### Memory Usage
- Efficient memory management
- Release resources when idle
- Monitor memory leaks
- Optimize large datasets

### Responsiveness
- UI thread never blocks
- Background tasks for heavy operations
- Progress indicators for long tasks
- Cancellable operations

## Window States

### Normal
- User-defined size and position
- Remember last state
- Minimum size enforced

### Maximized
- Full screen minus taskbar/dock
- Restore to previous size
- Platform-specific behavior

### Minimized
- To taskbar/dock
- Restore to previous state
- Show in window list

### Full Screen
- Hide all chrome
- Escape to exit
- macOS: Separate space
- Windows: Borderless maximized

## Dialogs & Modals

### Modal Dialogs
- Block parent window
- Center on parent
- Dim parent window
- Escape to close (if safe)

### Non-Modal Dialogs
- Float above parent
- Can interact with parent
- Preferences, inspectors

### File Dialogs
- Native file picker
- Filters by file type
- Multiple selection support
- Remember last directory

## Accessibility

### Screen Readers
- Proper ARIA labels
- Semantic HTML
- Keyboard navigation
- Focus management

### High Contrast
- Respect system high contrast mode
- Sufficient color contrast
- Border outlines visible

### Keyboard Only
- All features accessible via keyboard
- Visible focus indicators
- Logical tab order
- Keyboard shortcuts documented

## Updates

### Auto-Update
- Check for updates on launch
- Background download
- Prompt to install
- Release notes

### Manual Update
- Check for updates menu item
- Download progress
- Install and restart

## Best Practices

### Do:
- Use native system controls when possible
- Respect system preferences
- Provide keyboard shortcuts
- Support drag & drop
- Remember window state
- Use system notifications
- Integrate with system menu
- Handle offline gracefully

### Don't:
- Force window size/position
- Ignore system theme
- Block UI thread
- Use non-standard shortcuts
- Require internet for basic features
- Auto-update without permission
- Use custom scrollbars (unless necessary)
- Ignore platform conventions

