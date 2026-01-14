# Linear Design System

## Overview

Linear is widely considered the gold standard for modern SaaS design. Their interface is the benchmark for "not looking like AI slop" - minimal, intentional, and distinctively human-crafted.

**Website**: https://linear.app

## Why Reference Linear

1. **Anti-AI aesthetic** - Looks unmistakably human-designed
2. **Minimal but not empty** - Every element earns its place
3. **Dark mode excellence** - Best-in-class dark UI
4. **Micro-interactions** - Polished, delightful details
5. **Information density** - Efficient without feeling cramped
6. **Keyboard-first** - Power user focused

## Key Design Principles

### 1. Purposeful Minimalism
- Remove until it breaks, then add back one thing
- No decoration for decoration's sake
- Visual hierarchy through spacing, not color

### 2. Dark Mode Native
- Designed dark-first, not adapted
- Subtle color on dark backgrounds
- Glows instead of shadows

### 3. Speed as Feature
- Instant feedback
- Optimistic updates
- Keyboard shortcuts everywhere

### 4. Craft in Details
- Subtle gradients
- Precise animations
- Thoughtful micro-interactions

## Color System

### Dark Theme (Primary)

```css
:root {
  /* Backgrounds - layered grays */
  --linear-bg-base: #0a0a0b;
  --linear-bg-elevated: #111113;
  --linear-bg-surface: #18181b;
  --linear-bg-hover: #1f1f23;
  --linear-bg-active: #27272b;
  
  /* Text */
  --linear-text-primary: #f4f4f5;
  --linear-text-secondary: #a1a1aa;
  --linear-text-tertiary: #71717a;
  --linear-text-disabled: #52525b;
  
  /* Borders */
  --linear-border-subtle: #27272a;
  --linear-border-default: #3f3f46;
  --linear-border-strong: #52525b;
  
  /* Accent - Purple/Violet */
  --linear-accent: #8b5cf6;
  --linear-accent-hover: #a78bfa;
  --linear-accent-subtle: rgba(139, 92, 246, 0.15);
  
  /* Status Colors */
  --linear-success: #22c55e;
  --linear-warning: #eab308;
  --linear-error: #ef4444;
  --linear-info: #3b82f6;
}
```

### Light Theme

```css
[data-theme="light"] {
  --linear-bg-base: #ffffff;
  --linear-bg-elevated: #fafafa;
  --linear-bg-surface: #f4f4f5;
  --linear-bg-hover: #e4e4e7;
  --linear-bg-active: #d4d4d8;
  
  --linear-text-primary: #18181b;
  --linear-text-secondary: #52525b;
  --linear-text-tertiary: #71717a;
  
  --linear-border-subtle: #e4e4e7;
  --linear-border-default: #d4d4d8;
}
```

### Priority Colors

Linear uses specific colors for issue priorities:

```css
--linear-priority-urgent: #ef4444;  /* Red */
--linear-priority-high: #f97316;    /* Orange */
--linear-priority-medium: #eab308;  /* Yellow */
--linear-priority-low: #6b7280;     /* Gray */
--linear-priority-none: #3f3f46;    /* Dark gray */
```

### Status Colors

```css
--linear-status-backlog: #6b7280;
--linear-status-todo: #a1a1aa;
--linear-status-in-progress: #3b82f6;
--linear-status-done: #22c55e;
--linear-status-cancelled: #ef4444;
```

## Typography

### Font Stack

Linear uses Inter as primary font:

```css
--linear-font-sans: "Inter", -apple-system, BlinkMacSystemFont, 
                    "Segoe UI", Roboto, sans-serif;
--linear-font-mono: "JetBrains Mono", "SF Mono", Monaco, 
                    Consolas, monospace;
```

### Type Scale

```css
--linear-text-xs: 11px;
--linear-text-sm: 12px;
--linear-text-base: 13px;  /* Note: smaller than typical 16px */
--linear-text-md: 14px;
--linear-text-lg: 16px;
--linear-text-xl: 18px;
--linear-text-2xl: 20px;
--linear-text-3xl: 24px;
```

### Font Weights

```css
--linear-font-normal: 400;
--linear-font-medium: 500;
--linear-font-semibold: 600;
```

## Spacing

Tight, efficient spacing:

```css
--linear-space-1: 4px;
--linear-space-2: 8px;
--linear-space-3: 12px;
--linear-space-4: 16px;
--linear-space-5: 20px;
--linear-space-6: 24px;
--linear-space-8: 32px;
--linear-space-10: 40px;
--linear-space-12: 48px;
```

## Border Radius

Subtle, consistent radius:

```css
--linear-radius-sm: 4px;
--linear-radius-md: 6px;
--linear-radius-lg: 8px;
--linear-radius-xl: 12px;
```

## Shadows & Glows

In dark mode, Linear uses glows instead of shadows:

```css
/* Dark mode - glows */
--linear-glow-sm: 0 0 0 1px rgba(255, 255, 255, 0.05);
--linear-glow-md: 0 0 0 1px rgba(255, 255, 255, 0.1), 
                  0 4px 12px rgba(0, 0, 0, 0.4);
--linear-glow-accent: 0 0 0 1px var(--linear-accent), 
                      0 0 20px rgba(139, 92, 246, 0.3);

/* Light mode - shadows */
--linear-shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
--linear-shadow-md: 0 4px 12px rgba(0, 0, 0, 0.1);
```

## Component Patterns

### Button

```css
.linear-button {
  height: 28px;
  padding: 0 10px;
  font-size: 12px;
  font-weight: 500;
  border-radius: 6px;
  transition: all 0.15s ease;
}

/* Primary */
.linear-button-primary {
  background: var(--linear-accent);
  color: white;
}

.linear-button-primary:hover {
  background: var(--linear-accent-hover);
}

/* Secondary */
.linear-button-secondary {
  background: var(--linear-bg-surface);
  color: var(--linear-text-primary);
  border: 1px solid var(--linear-border-subtle);
}

/* Ghost */
.linear-button-ghost {
  background: transparent;
  color: var(--linear-text-secondary);
}

.linear-button-ghost:hover {
  background: var(--linear-bg-hover);
  color: var(--linear-text-primary);
}
```

### Input

```css
.linear-input {
  height: 32px;
  padding: 0 10px;
  font-size: 13px;
  background: var(--linear-bg-surface);
  border: 1px solid var(--linear-border-subtle);
  border-radius: 6px;
  color: var(--linear-text-primary);
}

.linear-input:focus {
  border-color: var(--linear-accent);
  box-shadow: var(--linear-glow-accent);
  outline: none;
}

.linear-input::placeholder {
  color: var(--linear-text-tertiary);
}
```

### Card / Panel

```css
.linear-panel {
  background: var(--linear-bg-elevated);
  border: 1px solid var(--linear-border-subtle);
  border-radius: 8px;
  padding: 16px;
}
```

### List Item

```css
.linear-list-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 8px 12px;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.1s ease;
}

.linear-list-item:hover {
  background: var(--linear-bg-hover);
}

.linear-list-item.selected {
  background: var(--linear-accent-subtle);
}
```

## Distinctive Characteristics

### What Makes Linear Look "Not AI"

1. **Smaller base font** - 13px, not 16px
2. **Tighter spacing** - Efficient, not cramped
3. **Dark-first design** - Not an afterthought
4. **Purple accent** - Not generic blue
5. **Glows over shadows** - In dark mode
6. **Subtle borders** - 1px, barely visible
7. **Keyboard indicators** - Shortcuts shown inline
8. **Status colors** - Meaningful, not decorative

### Visual Signatures

- **Layered dark grays** - Multiple elevation levels
- **Purple/violet accent** - Distinctive brand color
- **Compact components** - 28-32px heights
- **Subtle hover states** - Background change only
- **Icon + text** - Consistent pairing
- **Monospace for IDs** - Technical precision

## Micro-Interactions

### Hover States
- Background color shift (not border change)
- 100-150ms transition
- Subtle, not dramatic

### Focus States
- Accent color border
- Subtle glow effect
- No outline, custom ring

### Loading States
- Skeleton with subtle pulse
- Optimistic updates
- Instant feedback

### Keyboard Navigation
- Visible shortcuts (⌘K, ⌘/)
- Focus rings
- Arrow key navigation

## Best Practices

### Do:
- Design dark mode first
- Use smaller font sizes (12-14px)
- Keep spacing tight but readable
- Use purple/violet as accent
- Show keyboard shortcuts
- Make hover states subtle
- Use glows in dark mode

### Don't:
- Use heavy shadows in dark mode
- Make components too large
- Use bright colors liberally
- Ignore keyboard navigation
- Over-animate interactions
- Use generic blue accent
- Waste vertical space

## Integration with MBA Design Rules

When applying Linear's aesthetic:

1. **Go dark** - Design dark mode first
2. **Shrink fonts** - 13-14px base, not 16px
3. **Tighten spacing** - More compact than typical
4. **Change accent** - Purple instead of blue
5. **Use glows** - Replace shadows in dark mode
6. **Add shortcuts** - Show keyboard hints
7. **Reduce radius** - 4-8px, not 12-16px

## Resources

- **Linear App**: https://linear.app
- **Linear Blog**: https://linear.app/blog
- **Design Inspiration**: https://linear.app/now/how-we-redesigned-the-linear-ui
- **Figma Community**: Search "Linear UI Kit"
