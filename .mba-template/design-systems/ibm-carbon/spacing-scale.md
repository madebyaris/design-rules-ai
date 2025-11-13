# IBM Carbon - Spacing Scale

## Overview
Carbon uses a 2px base unit system, providing fine-grained control over spacing.

## Spacing Scale (2px base)

### Tokens
- **spacing-01**: 2px (0.125rem) - Minimal spacing
- **spacing-02**: 4px (0.25rem) - Tight spacing
- **spacing-03**: 8px (0.5rem) - Small spacing
- **spacing-04**: 12px (0.75rem) - Compact spacing
- **spacing-05**: 16px (1rem) - Standard spacing
- **spacing-06**: 24px (1.5rem) - Medium spacing
- **spacing-07**: 32px (2rem) - Large spacing
- **spacing-08**: 40px (2.5rem) - Extra large spacing
- **spacing-09**: 48px (3rem) - Section spacing
- **spacing-10**: 64px (4rem) - Large section spacing
- **spacing-11**: 80px (5rem) - Extra large section
- **spacing-12**: 96px (6rem) - Maximum spacing
- **spacing-13**: 160px (10rem) - Exceptional spacing

## Layout Tokens

### Container Padding
- **Mobile**: spacing-05 (16px)
- **Tablet**: spacing-06 (24px)
- **Desktop**: spacing-07 (32px)
- **Large Desktop**: spacing-08 (40px)

### Component Spacing

#### Buttons
- Padding horizontal: spacing-05 (16px)
- Padding vertical: spacing-03 (8px) for small, spacing-04 (12px) for default
- Gap between buttons: spacing-03 (8px)

#### Forms
- Label to input: spacing-02 (4px)
- Input to input: spacing-05 (16px)
- Field group spacing: spacing-06 (24px)

#### Cards
- Padding: spacing-05 (16px) or spacing-06 (24px)
- Gap between cards: spacing-05 (16px)

#### Tables
- Cell padding: spacing-03 (8px) horizontal, spacing-02 (4px) vertical
- Row spacing: spacing-01 (2px)

## Grid System

### 2x Grid
All elements align to a 2px grid for pixel-perfect consistency.

### 16-Column Grid
- **Mobile (320-671px)**: 16px margins, 16px gutters
- **Tablet (672-1055px)**: 16px margins, 16px gutters
- **Desktop (1056-1311px)**: 16px margins, 16px gutters
- **Large (1312-1583px)**: 16px margins, 16px gutters
- **X-Large (1584px+)**: 24px margins, 24px gutters

## Vertical Rhythm

### Typography Spacing
- Paragraph spacing: spacing-05 (16px)
- Heading to content: spacing-05 (16px)
- Section spacing: spacing-07 to spacing-09 (32-48px)

## Responsive Adjustments
- Maintain 2px grid alignment at all breakpoints
- Scale spacing proportionally for smaller screens
- Never use arbitrary pixel values

## Component-Specific Guidelines

### Navigation
- Nav item padding: spacing-04 (12px) vertical, spacing-05 (16px) horizontal
- Nav item gap: spacing-01 (2px)

### Modals
- Padding: spacing-06 (24px) or spacing-07 (32px)
- Content spacing: spacing-05 (16px)

### Lists
- List item padding: spacing-04 (12px)
- Gap between items: spacing-03 (8px)

