---
name: mba-build-component
description: Generate a production-ready component with proper structure and states
---

# MBA Build Component

Generate a semantic, accessible, production-ready component following MBA design system rules.

## Arguments

- `component_name` (required): Name of component (e.g., "button", "card", "navigation", "data-table")
- `framework` (optional): html|react|vue|svelte|web-component - default: html
- `variants` (optional): Comma-separated list (e.g., "primary,secondary,ghost") - default: based on component
- `sizes` (optional): Comma-separated list (e.g., "small,medium,large") - default: "medium"
- `theme` (optional): enterprise|neutral|editorial|playful - default: enterprise
- `with_examples` (optional): true|false - include usage examples - default: true

## Instructions

1. **Review Component Patterns**:
   - Read `.cursor/rules/50-components.mdc`
   - Reference `.mba-template/design-systems/*/components.md`
   - Check `.cursor/rules/70-accessibility.mdc`

2. **Generate Component Structure**:
   
   **HTML/CSS:**
   ```html
   <!-- Semantic HTML with proper ARIA -->
   <button class="btn btn--primary btn--medium" type="button">
     <span class="btn__icon"><!-- optional --></span>
     <span class="btn__label">Button Text</span>
   </button>
   ```
   
   **React:**
   ```jsx
   interface ButtonProps {
     variant?: 'primary' | 'secondary' | 'ghost';
     size?: 'small' | 'medium' | 'large';
     disabled?: boolean;
     onClick?: () => void;
     children: React.ReactNode;
   }
   
   export const Button: React.FC<ButtonProps> = ({ ... }) => { ... }
   ```

3. **Include All States**:
   - Default
   - Hover
   - Active/Pressed
   - Focus (keyboard navigation)
   - Disabled
   - Loading (if applicable)
   - Error (if applicable)

4. **Implement Accessibility**:
   - Proper semantic HTML elements
   - ARIA labels where needed
   - Keyboard navigation support
   - Focus indicators (2px outline)
   - Screen reader support
   - Touch targets (44px × 44px minimum for mobile)

5. **Apply Theme**:
   - Use design tokens from `tokens.css`
   - Apply theme-specific spacing/sizing
   - Ensure WCAG AA contrast
   - Platform-appropriate patterns

6. **Generate Documentation**:
   - Component description
   - Props/attributes
   - Variants and sizes
   - Usage examples
   - Accessibility notes
   - Do's and don'ts

7. **Create Examples**:
   - Basic usage
   - All variants
   - All sizes
   - Different states
   - Common patterns
   - Edge cases

## Common Components

### Button
- Variants: primary, secondary, tertiary/ghost, danger
- Sizes: small (32px), medium (40px), large (48px)
- States: default, hover, active, focus, disabled, loading

### Input
- Types: text, email, password, number, search, textarea
- States: default, hover, focus, error, disabled, readonly
- Features: label, placeholder, help text, error message, icons

### Card
- Variants: flat (border only), elevated (shadow), interactive
- Sections: header, body, footer
- Features: title, actions, media, padding

### Table
- Features: sortable columns, row hover, selection, pagination
- Responsive: card-based on mobile
- Accessibility: proper th/td, scope attributes

### Navigation
- Types: top nav, side nav, bottom tabs, breadcrumbs
- States: active, hover, focus
- Responsive: hamburger menu on mobile

### Modal/Dialog
- Sizes: small (480px), medium (600px), large (800px)
- Features: overlay, header, body, footer, close button
- Behavior: focus trap, escape to close, return focus

## Output Files

1. Component file:
   - `components/{component_name}.{html|jsx|vue|svelte}`
   - `components/{component_name}.css` (if separate)

2. Documentation:
   - `components/{component_name}.md`

3. Examples:
   - `examples/{component_name}-example.{html|jsx|vue|svelte}`

## Quality Checks

- [ ] Semantic HTML structure
- [ ] All variants implemented
- [ ] All sizes implemented
- [ ] All states included (hover, focus, disabled, etc.)
- [ ] ARIA labels where needed
- [ ] Keyboard navigation works
- [ ] Focus indicators visible (2px outline)
- [ ] Touch targets adequate (44px+ for mobile)
- [ ] WCAG AA contrast ratios
- [ ] Design tokens used (no hardcoded values)
- [ ] Responsive behavior defined
- [ ] Documentation complete
- [ ] Examples provided

## Example Usage

```
/mba-build-component component_name="button" framework="react" variants="primary,secondary,ghost,danger" sizes="small,medium,large" theme="enterprise" with_examples="true"
```

This will generate a React button component with all variants, sizes, and comprehensive examples.

## Anti-Patterns to Avoid

Reference `.cursor/rules/80-anti-ai-patterns.mdc`:
- No random spacing values
- No excessive gradients
- No over-rounded corners (>16px)
- No low contrast text
- No missing states (hover, focus)
- No tiny touch targets
- No divs for buttons

