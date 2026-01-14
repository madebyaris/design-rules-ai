# shadcn/ui Design System

## Overview

shadcn/ui is the de facto standard for modern React applications. It's not a component library you install - it's a collection of re-usable components you copy into your project and customize.

**Website**: https://ui.shadcn.com

## Why Reference shadcn/ui

1. **Copy-paste philosophy** - Components are yours to modify
2. **Built on Radix UI** - Accessible primitives by default
3. **Tailwind CSS** - Utility-first styling
4. **CSS Variables** - Easy theming with design tokens
5. **TypeScript** - Full type safety
6. **Widely adopted** - Industry standard for React apps

## Key Design Principles

### 1. Minimal by Default
- Components are unstyled or minimally styled
- No visual opinions forced on you
- Build your own aesthetic on top

### 2. Accessible First
- Built on Radix UI primitives
- Keyboard navigation out of the box
- Screen reader support
- Focus management

### 3. Composable
- Small, focused components
- Combine to build complex UIs
- No prop drilling nightmares

## Color System (CSS Variables)

shadcn/ui uses a semantic color system with CSS variables:

```css
:root {
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;
  
  --card: 0 0% 100%;
  --card-foreground: 222.2 84% 4.9%;
  
  --popover: 0 0% 100%;
  --popover-foreground: 222.2 84% 4.9%;
  
  --primary: 222.2 47.4% 11.2%;
  --primary-foreground: 210 40% 98%;
  
  --secondary: 210 40% 96.1%;
  --secondary-foreground: 222.2 47.4% 11.2%;
  
  --muted: 210 40% 96.1%;
  --muted-foreground: 215.4 16.3% 46.9%;
  
  --accent: 210 40% 96.1%;
  --accent-foreground: 222.2 47.4% 11.2%;
  
  --destructive: 0 84.2% 60.2%;
  --destructive-foreground: 210 40% 98%;
  
  --border: 214.3 31.8% 91.4%;
  --input: 214.3 31.8% 91.4%;
  --ring: 222.2 84% 4.9%;
  
  --radius: 0.5rem;
}

.dark {
  --background: 222.2 84% 4.9%;
  --foreground: 210 40% 98%;
  /* ... dark mode overrides */
}
```

### Color Naming Convention
- `--background` / `--foreground` - Page background and text
- `--card` / `--card-foreground` - Card surfaces
- `--primary` / `--primary-foreground` - Primary actions
- `--secondary` / `--secondary-foreground` - Secondary actions
- `--muted` / `--muted-foreground` - Subtle backgrounds and text
- `--accent` / `--accent-foreground` - Highlights
- `--destructive` / `--destructive-foreground` - Danger/delete actions

## Typography

shadcn/ui doesn't enforce typography - use your own font stack:

```css
/* Common setup */
--font-sans: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, 
             "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
--font-mono: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Monaco, 
             Consolas, "Liberation Mono", "Courier New", monospace;
```

### Recommended Type Scale
- `text-xs`: 12px
- `text-sm`: 14px
- `text-base`: 16px
- `text-lg`: 18px
- `text-xl`: 20px
- `text-2xl`: 24px
- `text-3xl`: 30px
- `text-4xl`: 36px

## Spacing

Uses Tailwind's spacing scale (4px base):

```
0: 0px
1: 4px
2: 8px
3: 12px
4: 16px
5: 20px
6: 24px
8: 32px
10: 40px
12: 48px
16: 64px
```

## Border Radius

Single radius variable for consistency:

```css
--radius: 0.5rem; /* 8px - adjust per project */
```

Usage:
- `rounded-sm`: calc(var(--radius) - 4px)
- `rounded-md`: calc(var(--radius) - 2px)
- `rounded-lg`: var(--radius)
- `rounded-xl`: calc(var(--radius) + 4px)

## Component Patterns

### Button
```tsx
<Button variant="default">Default</Button>
<Button variant="destructive">Destructive</Button>
<Button variant="outline">Outline</Button>
<Button variant="secondary">Secondary</Button>
<Button variant="ghost">Ghost</Button>
<Button variant="link">Link</Button>

<Button size="default">Default</Button>
<Button size="sm">Small</Button>
<Button size="lg">Large</Button>
<Button size="icon">Icon</Button>
```

### Input
```tsx
<Input type="email" placeholder="Email" />
<Input disabled placeholder="Disabled" />
```

### Card
```tsx
<Card>
  <CardHeader>
    <CardTitle>Title</CardTitle>
    <CardDescription>Description</CardDescription>
  </CardHeader>
  <CardContent>Content</CardContent>
  <CardFooter>Footer</CardFooter>
</Card>
```

### Dialog (Modal)
```tsx
<Dialog>
  <DialogTrigger>Open</DialogTrigger>
  <DialogContent>
    <DialogHeader>
      <DialogTitle>Title</DialogTitle>
      <DialogDescription>Description</DialogDescription>
    </DialogHeader>
    {/* Content */}
    <DialogFooter>
      <Button>Save</Button>
    </DialogFooter>
  </DialogContent>
</Dialog>
```

## Dark Mode

shadcn/ui supports dark mode via CSS class:

```tsx
// Toggle dark mode
document.documentElement.classList.toggle('dark')
```

All components automatically adapt using CSS variables.

## Accessibility Features

Built on Radix UI, shadcn/ui components include:

- **Keyboard navigation** - Arrow keys, Enter, Escape
- **Focus management** - Proper focus trapping in modals
- **ARIA attributes** - Correct roles and labels
- **Screen reader support** - Announcements for dynamic content
- **Reduced motion** - Respects `prefers-reduced-motion`

## Best Practices

### Do:
- Use CSS variables for theming
- Keep components minimal
- Compose small components into larger ones
- Use semantic color names
- Test keyboard navigation
- Support dark mode

### Don't:
- Over-customize base components
- Add too many variants
- Ignore accessibility
- Use hardcoded colors
- Skip dark mode support

## Integration with MBA Design Rules

When using shadcn/ui with MBA rules:

1. **Map colors** - Align shadcn variables with MBA tokens
2. **Use spacing scale** - Both use similar 4px/8px base
3. **Keep radius consistent** - Use MBA's 4px, 8px, 12px scale
4. **Follow accessibility** - Both prioritize WCAG AA

## Resources

- **Documentation**: https://ui.shadcn.com/docs
- **Components**: https://ui.shadcn.com/docs/components
- **Themes**: https://ui.shadcn.com/themes
- **Examples**: https://ui.shadcn.com/examples
- **GitHub**: https://github.com/shadcn-ui/ui
