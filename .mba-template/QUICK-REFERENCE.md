# MBA Design Quick Reference

Copy-paste values for fast implementation.

## Spacing Scale
```
4px | 8px | 12px | 16px | 20px | 24px | 32px | 40px | 48px | 64px | 80px | 96px
```

## Border Radius
```
4px   - buttons, inputs
8px   - cards
12px  - modals
9999px - pills/avatars
```

## Breakpoints
```css
@media (min-width: 640px)  { /* tablet */ }
@media (min-width: 768px)  { /* tablet landscape */ }
@media (min-width: 1024px) { /* desktop */ }
@media (min-width: 1280px) { /* large desktop */ }
```

## Animation Durations
```
100ms - hover/focus
200ms - buttons/inputs
300ms - modals/drawers
500ms - page transitions
```

## Touch Targets
```
44px × 44px - mobile minimum
32px × 32px - desktop minimum
```

## Icon Setup (Font Awesome)
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
```

## Common Icons
```html
<i class="fa-solid fa-user"></i>        <!-- user -->
<i class="fa-solid fa-xmark"></i>       <!-- close -->
<i class="fa-solid fa-plus"></i>        <!-- add -->
<i class="fa-solid fa-check"></i>       <!-- success -->
<i class="fa-solid fa-magnifying-glass"></i> <!-- search -->
<i class="fa-solid fa-gear"></i>        <!-- settings -->
<i class="fa-solid fa-trash"></i>       <!-- delete -->
<i class="fa-solid fa-pen"></i>         <!-- edit -->
```

## Button Template
```html
<button class="btn btn-primary">
  <i class="fa-solid fa-save" aria-hidden="true"></i>
  <span>Save Changes</span>
</button>
```

## Input Template
```html
<div class="form-field">
  <label for="email">Email</label>
  <input type="email" id="email" placeholder="you@example.com">
  <span class="help-text">We'll never share your email.</span>
</div>
```

## Card Template
```html
<div class="card">
  <div class="card-header">
    <h3>Card Title</h3>
  </div>
  <div class="card-body">
    <p>Card content goes here.</p>
  </div>
  <div class="card-footer">
    <button class="btn btn-secondary">Cancel</button>
    <button class="btn btn-primary">Save</button>
  </div>
</div>
```

## Focus State CSS
```css
:focus-visible {
  outline: 2px solid var(--color-interactive-primary);
  outline-offset: 2px;
}
```

## Reduced Motion CSS
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## System Font Stack
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
```

## Monospace Font Stack
```css
font-family: "SF Mono", "Cascadia Code", "Fira Code", Consolas, monospace;
```
