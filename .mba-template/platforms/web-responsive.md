# Web Responsive Design Guidelines

## Mobile-First Approach
Start with mobile design, then enhance for larger screens.

## Breakpoints (Standard)
- **Mobile**: 320-639px
- **Tablet**: 640-1023px
- **Desktop**: 1024-1439px
- **Large Desktop**: 1440px+

## Common Breakpoint Systems

### Tailwind CSS
- sm: 640px
- md: 768px
- lg: 1024px
- xl: 1280px
- 2xl: 1536px

### Bootstrap
- sm: 576px
- md: 768px
- lg: 992px
- xl: 1200px
- xxl: 1400px

### Material Design
- Compact: 0-599px
- Medium: 600-839px
- Expanded: 840px+

## Layout Patterns

### Mobile (< 640px)
- Single column layout
- Full-width components
- Stacked navigation (hamburger menu)
- Bottom tab bar for primary navigation
- Larger touch targets (44px minimum)
- Reduced spacing (16px margins)

### Tablet (640-1023px)
- 2-column layouts possible
- Side navigation appears
- Increased spacing (24px margins)
- Larger typography
- Grid layouts (2-3 columns)

### Desktop (1024px+)
- Multi-column layouts (3-4 columns)
- Persistent side navigation
- Hover states prominent
- Keyboard navigation important
- Maximum content width (1280-1440px)
- Generous spacing (32-40px margins)

## Responsive Typography

### Fluid Typography
```css
/* Example: 16px at 320px, 20px at 1440px */
font-size: clamp(1rem, 0.857rem + 0.357vw, 1.25rem);
```

### Scale by Breakpoint
- Mobile: Base size 14-16px
- Tablet: Base size 16px
- Desktop: Base size 16-18px

## Touch Targets

### Mobile/Tablet
- Minimum: 44px × 44px
- Recommended: 48px × 48px
- Spacing: 8px between targets

### Desktop
- Minimum: 32px × 32px (mouse precision)
- Hover states essential
- Focus indicators for keyboard

## Navigation Patterns

### Mobile
- Hamburger menu (top-left or top-right)
- Bottom tab bar (3-5 items)
- Full-screen menu overlay
- Swipe gestures

### Tablet
- Persistent side nav (collapsible)
- Top navigation bar
- Hybrid: hamburger + visible items

### Desktop
- Persistent side navigation
- Horizontal top navigation
- Mega menus for complex hierarchies
- Breadcrumbs for deep navigation

## Grid Systems

### Mobile
- 4-column grid
- 16px gutters
- 16px margins
- Full-width components common

### Tablet
- 8-column grid
- 16-24px gutters
- 24px margins
- 2-4 column layouts

### Desktop
- 12-column grid
- 24-32px gutters
- 32-40px margins
- 3-6 column layouts
- Max content width: 1280-1440px

## Images & Media

### Responsive Images
```html
<img srcset="image-320w.jpg 320w,
             image-640w.jpg 640w,
             image-1024w.jpg 1024w"
     sizes="(max-width: 640px) 100vw,
            (max-width: 1024px) 50vw,
            33vw"
     src="image-640w.jpg" alt="Description">
```

### Aspect Ratios
- Hero images: 16:9 (desktop), 4:3 (mobile)
- Thumbnails: 1:1 or 4:3
- Product images: 1:1 or 3:4

## Forms

### Mobile
- Full-width inputs
- Labels above inputs
- Large input fields (48px height)
- Native input types (date, tel, email)
- Minimal inline validation

### Desktop
- Multi-column forms possible
- Labels left or above
- Standard input height (40px)
- Inline validation helpful
- Keyboard shortcuts

## Tables

### Mobile
- Card-based layout (stacked)
- Horizontal scroll for data tables
- Collapsible rows
- Priority columns only

### Tablet/Desktop
- Full table layout
- Fixed headers on scroll
- Sortable columns
- Pagination or infinite scroll

## Performance

### Mobile Optimization
- Optimize images (WebP, AVIF)
- Lazy load below-fold content
- Minimize JavaScript
- Critical CSS inline
- Reduce HTTP requests

### Progressive Enhancement
- Core content without JavaScript
- Enhanced features with JS
- Graceful degradation
- Feature detection

## Accessibility

### All Devices
- Keyboard navigation
- Screen reader support
- ARIA labels
- Focus management
- Color contrast (WCAG AA)

### Mobile Specific
- Zoom support (no user-scalable=no)
- Orientation support
- Reduced motion support
- Touch-friendly spacing

## Testing

### Devices to Test
- iPhone (Safari)
- Android phone (Chrome)
- iPad (Safari)
- Desktop (Chrome, Firefox, Safari, Edge)

### Viewport Sizes
- 320px (small mobile)
- 375px (iPhone)
- 768px (tablet portrait)
- 1024px (tablet landscape)
- 1440px (desktop)
- 1920px (large desktop)

## Common Patterns

### Header
- Mobile: Logo + hamburger
- Tablet: Logo + primary nav + hamburger
- Desktop: Logo + full navigation + search

### Hero Section
- Mobile: Full-width, stacked content
- Tablet: 2-column (text + image)
- Desktop: Wide layout, larger typography

### Card Grid
- Mobile: 1 column
- Tablet: 2-3 columns
- Desktop: 3-4 columns

### Footer
- Mobile: Stacked sections, accordion
- Tablet: 2-3 columns
- Desktop: 4-5 columns

## CSS Techniques

### Media Queries
```css
/* Mobile first */
.element { /* mobile styles */ }

@media (min-width: 640px) {
  .element { /* tablet styles */ }
}

@media (min-width: 1024px) {
  .element { /* desktop styles */ }
}
```

### Container Queries (Modern)
```css
@container (min-width: 400px) {
  .card { /* styles when container is 400px+ */ }
}
```

### Responsive Units
- rem/em: Scalable with user preferences
- vw/vh: Viewport relative
- %: Parent relative
- clamp(): Fluid sizing with limits

