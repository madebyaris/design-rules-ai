# Vercel Geist Design System

## Overview

Geist is Vercel's design system, known for its clean, minimal aesthetic that prioritizes readability and developer experience. It's the visual language behind Vercel's products and the Geist font family.

**Website**: https://vercel.com/geist

## Why Reference Geist

1. **Minimal and clean** - No visual noise
2. **Developer-focused** - Designed for technical products
3. **Excellent typography** - Geist font family is beautiful
4. **High contrast** - Readable in all conditions
5. **Distinctive** - Doesn't look like generic AI output

## Key Design Principles

### 1. Clarity Over Decoration
- Remove unnecessary elements
- Every pixel serves a purpose
- White space is a feature, not empty space

### 2. Typography First
- Geist font family (Sans + Mono)
- Clear hierarchy through size and weight
- Generous line height for readability

### 3. Monochromatic Base
- Primarily black, white, and grays
- Color used sparingly for meaning
- High contrast for accessibility

### 4. Subtle Depth
- Minimal shadows
- Border-based separation
- Flat design with subtle elevation

## Typography

### Geist Font Family

**Geist Sans** - For UI and body text
- Clean, geometric sans-serif
- Optimized for screens
- Available on Google Fonts

**Geist Mono** - For code and technical content
- Designed for code readability
- Clear character distinction
- Ligature support

### Type Scale

```css
/* Geist type scale */
--font-size-11: 0.6875rem;  /* 11px - tiny labels */
--font-size-12: 0.75rem;    /* 12px - captions */
--font-size-13: 0.8125rem;  /* 13px - small text */
--font-size-14: 0.875rem;   /* 14px - body small */
--font-size-16: 1rem;       /* 16px - body */
--font-size-18: 1.125rem;   /* 18px - body large */
--font-size-20: 1.25rem;    /* 20px - heading 5 */
--font-size-24: 1.5rem;     /* 24px - heading 4 */
--font-size-32: 2rem;       /* 32px - heading 3 */
--font-size-40: 2.5rem;     /* 40px - heading 2 */
--font-size-48: 3rem;       /* 48px - heading 1 */
```

### Line Heights

```css
--line-height-16: 1rem;     /* 16px - tight */
--line-height-20: 1.25rem;  /* 20px - compact */
--line-height-24: 1.5rem;   /* 24px - normal */
--line-height-28: 1.75rem;  /* 28px - relaxed */
--line-height-32: 2rem;     /* 32px - loose */
```

### Font Weights

```css
--font-weight-normal: 400;
--font-weight-medium: 500;
--font-weight-semibold: 600;
--font-weight-bold: 700;
```

## Color System

### Light Mode

```css
:root {
  /* Backgrounds */
  --geist-background: #ffffff;
  --geist-background-secondary: #fafafa;
  
  /* Foregrounds */
  --geist-foreground: #000000;
  --geist-secondary: #666666;
  --geist-tertiary: #888888;
  
  /* Borders */
  --geist-border: #eaeaea;
  --geist-border-hover: #999999;
  
  /* Accents */
  --geist-success: #0070f3;
  --geist-error: #ee0000;
  --geist-warning: #f5a623;
  
  /* Selection */
  --geist-selection: #79ffe1;
}
```

### Dark Mode

```css
[data-theme="dark"] {
  --geist-background: #000000;
  --geist-background-secondary: #111111;
  
  --geist-foreground: #ffffff;
  --geist-secondary: #888888;
  --geist-tertiary: #666666;
  
  --geist-border: #333333;
  --geist-border-hover: #555555;
}
```

### Accent Colors

Geist uses blue as the primary accent:

```css
--geist-cyan: #79ffe1;
--geist-purple: #f81ce5;
--geist-blue: #0070f3;
--geist-pink: #ff0080;
--geist-orange: #f5a623;
--geist-violet: #7928ca;
```

## Spacing

Based on 4px unit:

```css
--geist-space-1: 4px;
--geist-space-2: 8px;
--geist-space-3: 12px;
--geist-space-4: 16px;
--geist-space-5: 20px;
--geist-space-6: 24px;
--geist-space-7: 28px;
--geist-space-8: 32px;
--geist-space-9: 36px;
--geist-space-10: 40px;
--geist-space-11: 44px;
--geist-space-12: 48px;
--geist-space-16: 64px;
--geist-space-20: 80px;
--geist-space-24: 96px;
```

## Border Radius

Minimal, consistent radius:

```css
--geist-radius: 5px;        /* Default */
--geist-radius-sm: 4px;     /* Small elements */
--geist-radius-lg: 8px;     /* Large elements */
--geist-radius-full: 9999px; /* Pills, avatars */
```

## Shadows

Subtle, functional shadows:

```css
--geist-shadow-small: 0 5px 10px rgba(0, 0, 0, 0.12);
--geist-shadow-medium: 0 8px 30px rgba(0, 0, 0, 0.12);
--geist-shadow-large: 0 30px 60px rgba(0, 0, 0, 0.12);
```

## Component Patterns

### Button

```css
.geist-button {
  height: 40px;
  padding: 0 16px;
  font-size: 14px;
  font-weight: 500;
  border-radius: 5px;
  transition: all 0.2s ease;
}

/* Primary */
.geist-button-primary {
  background: var(--geist-foreground);
  color: var(--geist-background);
  border: 1px solid var(--geist-foreground);
}

/* Secondary */
.geist-button-secondary {
  background: var(--geist-background);
  color: var(--geist-foreground);
  border: 1px solid var(--geist-border);
}

/* Ghost */
.geist-button-ghost {
  background: transparent;
  color: var(--geist-foreground);
  border: 1px solid transparent;
}
```

### Input

```css
.geist-input {
  height: 40px;
  padding: 0 12px;
  font-size: 14px;
  background: var(--geist-background);
  border: 1px solid var(--geist-border);
  border-radius: 5px;
  transition: border-color 0.2s ease;
}

.geist-input:focus {
  border-color: var(--geist-foreground);
  outline: none;
}
```

### Card

```css
.geist-card {
  background: var(--geist-background);
  border: 1px solid var(--geist-border);
  border-radius: 8px;
  padding: 24px;
}

.geist-card:hover {
  border-color: var(--geist-border-hover);
}
```

## Distinctive Characteristics

### What Makes Geist Look "Not AI"

1. **Monochromatic palette** - No rainbow colors
2. **Consistent 5px radius** - Not over-rounded
3. **High contrast** - Black on white, white on black
4. **Generous spacing** - Breathing room
5. **Typography focus** - Content is king
6. **Subtle borders** - Not heavy shadows
7. **Intentional color** - Blue accent used sparingly

### Visual Signatures

- **Black/white primary** - Not blue or purple
- **Thin borders** - 1px, subtle gray
- **No gradients** - Flat colors
- **Minimal icons** - Text-first approach
- **Code-friendly** - Monospace where appropriate

## Best Practices

### Do:
- Use Geist font family
- Keep color palette minimal
- Prioritize typography hierarchy
- Use borders over shadows
- Maintain high contrast
- Leave generous white space

### Don't:
- Add unnecessary color
- Use heavy shadows
- Over-round corners
- Crowd elements together
- Use decorative elements
- Sacrifice readability

## Integration with MBA Design Rules

When applying Geist principles:

1. **Simplify color** - Reduce to black, white, gray + one accent
2. **Use Geist fonts** - Or similar geometric sans-serif
3. **Flatten shadows** - Use borders for separation
4. **Increase contrast** - Darker text, cleaner backgrounds
5. **Add space** - More padding, more margin

## Resources

- **Geist Design System**: https://vercel.com/geist
- **Geist Font**: https://vercel.com/font
- **Google Fonts**: https://fonts.google.com/specimen/Geist
- **Figma Kit**: https://www.figma.com/community/file/1330020847221146106
