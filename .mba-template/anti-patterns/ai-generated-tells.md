# AI-Generated Design Tells - What to AVOID

## Visual Red Flags

### 1. Excessive Gradients
**❌ Bad:**
- Gradients on every element
- Rainbow gradients without purpose
- Multiple gradient directions in one view
- Gradients on text (hard to read)

**✅ Good:**
- Gradients used sparingly for emphasis
- Subtle, purposeful gradients (brand, CTA)
- Consistent gradient direction
- Solid colors for text

### 2. Over-Rounded Corners
**❌ Bad:**
- Border radius > 16px on small elements
- Inconsistent radius values (8px, 12px, 15px, 20px all mixed)
- Perfectly circular buttons for non-icon buttons
- Rounded corners on everything

**✅ Good:**
- Consistent radius scale (4px, 8px, 12px, 16px)
- Smaller radius for compact UIs
- Larger radius for spacious UIs
- Strategic use of sharp vs rounded

### 3. Random Spacing
**❌ Bad:**
- Mixing 7px, 13px, 19px, 23px spacing
- No consistent spacing scale
- Arbitrary pixel values
- Uneven padding on similar elements

**✅ Good:**
- 4px or 8px base unit
- Consistent scale (4, 8, 12, 16, 24, 32, 48)
- Same spacing for same hierarchy
- Mathematically related values

### 4. Low Contrast Text
**❌ Bad:**
- Light gray text on white background
- #999 on #FFF (3:1 ratio)
- Colored text without contrast check
- Thin fonts with low contrast

**✅ Good:**
- WCAG AA minimum (4.5:1 for body text)
- Dark text on light backgrounds
- Sufficient weight for small text
- Test with contrast checker

### 5. Generic Placeholder Content
**❌ Bad:**
- "Lorem ipsum dolor sit amet..."
- "Click here" buttons
- "Product Name" as title
- "Description goes here"
- Generic user names (John Doe, Jane Smith)

**✅ Good:**
- Realistic company/product names
- Descriptive button labels
- Actual product titles
- Meaningful descriptions
- Diverse, realistic names

## Layout Red Flags

### 6. Centered Everything
**❌ Bad:**
- All text centered
- Buttons centered in cards
- Form labels centered
- Navigation items centered (except intentional)

**✅ Good:**
- Left-aligned text for readability
- Right-aligned numbers/dates
- Centered only for specific purposes (hero, modals)
- Consistent alignment patterns

### 7. Inconsistent Component Sizing
**❌ Bad:**
- Buttons with random heights (34px, 38px, 42px)
- Inputs different sizes in same form
- Icons varying from 18px to 24px to 28px
- No size system

**✅ Good:**
- Defined size scale (small, medium, large)
- Consistent heights (32px, 40px, 48px)
- Icon sizes: 16px, 20px, 24px
- Same size for same hierarchy

### 8. No Visual Hierarchy
**❌ Bad:**
- All text same size
- No weight variation
- Everything equally prominent
- Flat, monotonous layout

**✅ Good:**
- Clear heading sizes (H1 > H2 > H3)
- Weight for emphasis (regular, medium, bold)
- Size and color for hierarchy
- Clear primary/secondary actions

## Color Red Flags

### 9. Rainbow Colors Without Purpose
**❌ Bad:**
- Using 8+ colors in one interface
- Random color assignments
- Bright, saturated colors everywhere
- No semantic meaning to colors

**✅ Good:**
- Limited palette (2-3 accent colors)
- Semantic colors (red=error, green=success)
- Neutral base with color accents
- Consistent color roles

### 10. Inconsistent Color Usage
**❌ Bad:**
- Primary button blue on one page, green on another
- Error messages in different shades of red
- Links in multiple colors
- No color system

**✅ Good:**
- Consistent primary color
- Same semantic colors throughout
- Defined color roles
- Color tokens/variables

## Typography Red Flags

### 11. Too Many Fonts
**❌ Bad:**
- 3+ font families
- Decorative fonts for body text
- Script fonts for UI elements
- No font hierarchy

**✅ Good:**
- 1-2 font families maximum
- Sans-serif for UI
- Serif optional for editorial
- Clear type scale

### 12. Poor Line Length
**❌ Bad:**
- Text spanning full width (150+ characters)
- Very short lines (20-30 characters)
- No max-width on paragraphs
- Hard to read text blocks

**✅ Good:**
- 50-75 characters per line
- Max-width: 65ch for readability
- Appropriate column width
- Comfortable reading experience

## Interaction Red Flags

### 13. No Hover/Focus States
**❌ Bad:**
- Buttons look same on hover
- No focus indicators
- Links don't change on hover
- No visual feedback

**✅ Good:**
- Clear hover states
- Visible focus outlines (2px minimum)
- Active states for buttons
- Consistent interaction feedback

### 14. Tiny Touch Targets
**❌ Bad:**
- Buttons < 32px height
- Links too close together
- Small icons without padding
- Mobile UI with desktop sizing

**✅ Good:**
- Minimum 44px × 44px for touch
- Adequate spacing between targets
- Larger targets on mobile
- Easy to tap/click

## Content Red Flags

### 15. Unrealistic Data
**❌ Bad:**
- All values exactly 100, 200, 300
- Perfect round numbers everywhere
- Dates all on same day
- Suspiciously clean data

**✅ Good:**
- Realistic, varied numbers
- Mixed decimal values
- Varied dates and times
- Plausible data patterns

### 16. No Empty States
**❌ Bad:**
- Tables always full
- No error handling shown
- No loading states
- Perfect scenarios only

**✅ Good:**
- Empty state designs
- Error messages
- Loading indicators
- Edge case handling

## Professional Design Principles

### Do:
- Use consistent spacing scale
- Maintain visual hierarchy
- Follow accessibility standards
- Use realistic content
- Test on actual devices
- Reference established design systems
- Keep it simple and purposeful

### Don't:
- Over-design with effects
- Use random values
- Ignore accessibility
- Use placeholder text
- Skip user testing
- Reinvent common patterns
- Add decoration without purpose

