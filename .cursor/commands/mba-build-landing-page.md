---
name: mba-build-landing-page
description: Generate a professional landing page with proper structure and content
---

# MBA Build Landing Page

Generate a complete, professional landing page with semantic structure, realistic content, and conversion-focused design.

## Arguments

- `product_name` (required): Name of the product/service (e.g., "Acme Analytics Platform")
- `industry` (optional): Industry/category (e.g., "analytics", "fintech", "saas", "ecommerce") - default: "saas"
- `sections` (optional): Comma-separated list - default: "hero,social-proof,features,how-it-works,pricing,faq,cta"
- `theme` (optional): enterprise|neutral|editorial|playful - default: neutral
- `cta_text` (optional): Primary call-to-action text - default: "Get Started"
- `platform` (optional): web|mobile - default: web

## Instructions

1. **Review Page Patterns**:
   - Read `.cursor/rules/60-pages-templates.mdc`
   - Reference `.mba-template/patterns/landing-page-sections.md`
   - Check `.cursor/rules/10-visual-hierarchy.mdc`

2. **Generate Page Structure**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>{product_name} - {tagline}</title>
     <meta name="description" content="{description}">
   </head>
   <body>
     <header><!-- Navigation --></header>
     <main>
       <section class="hero"><!-- Hero section --></section>
       <section class="social-proof"><!-- Logos/testimonials --></section>
       <section class="features"><!-- Features grid --></section>
       <section class="how-it-works"><!-- Process steps --></section>
       <section class="pricing"><!-- Pricing tiers --></section>
       <section class="faq"><!-- FAQ accordion --></section>
       <section class="cta"><!-- Final CTA --></section>
     </main>
     <footer><!-- Footer --></footer>
   </body>
   </html>
   ```

3. **Hero Section** (60-80vh):
   - **Headline**: Clear value proposition (< 60 chars)
     - Example: "Turn Data Into Decisions in Minutes"
   - **Subheadline**: Supporting detail (2-3 sentences)
     - Example: "Acme Analytics helps teams visualize complex data with intuitive dashboards. No coding required. Start analyzing in under 5 minutes."
   - **Primary CTA**: Prominent button (e.g., "Start Free Trial")
   - **Secondary CTA**: Alternative action (e.g., "Watch Demo")
   - **Visual**: Product screenshot, illustration, or hero image
   - **Trust indicators**: "No credit card required" or "14-day free trial"

4. **Social Proof Section**:
   - **Customer logos**: 4-8 well-known companies (grayscale)
   - **Testimonials**: 2-3 quotes with:
     - Customer photo (48-64px avatar)
     - Quote (2-3 sentences)
     - Name, title, company
   - **Stats**: Key metrics
     - "10,000+ teams trust Acme"
     - "4.8/5 average rating"
     - "99.9% uptime"

5. **Features Section** (2-4 columns):
   - **Icon**: 32-48px per feature
   - **Title**: 18-24px, semibold
   - **Description**: 2-3 sentences
   - Examples:
     - "Real-Time Dashboards" - "See your data update instantly..."
     - "Custom Reports" - "Build reports tailored to your needs..."
     - "Team Collaboration" - "Share insights with your team..."

6. **How It Works** (3-4 steps):
   - Step numbers (large, prominent)
   - Step title
   - Step description
   - Optional illustration

7. **Pricing Section** (if included):
   - 2-3 tiers (Starter, Pro, Enterprise)
   - Price (realistic: $29/mo, $99/mo, Custom)
   - Features list (5-8 items per tier)
   - CTA button per tier
   - Highlight recommended tier

8. **FAQ Section**:
   - 5-8 common questions
   - Accordion pattern
   - Clear, helpful answers

9. **CTA Section**:
   - Headline: "Ready to get started?"
   - Subheadline: Brief encouragement
   - Large CTA button
   - Trust indicators
   - Contrasting background

10. **Footer**:
    - Logo
    - Navigation links (Product, Company, Resources, Legal)
    - Social media links
    - Copyright
    - Contact info

11. **Content Guidelines**:
    - **NO Lorem Ipsum** - use realistic, industry-appropriate content
    - **Specific benefits** - not generic "best solution"
    - **Real numbers** - "$1.2M saved", "45% faster", "10,000+ users"
    - **Action-oriented** - "Start analyzing", not "Click here"
    - **Conversational tone** - friendly but professional

12. **Responsive Design**:
    - Mobile: Single column, stacked sections
    - Tablet: 2 columns where appropriate
    - Desktop: Full layout with max-width 1280-1440px

13. **Accessibility**:
    - Semantic landmarks (header, nav, main, section, footer)
    - Proper heading hierarchy (H1 → H2 → H3)
    - Alt text for images
    - WCAG AA contrast
    - Keyboard navigation
    - Focus indicators

## Output Files

1. `pages/landing.html` - Complete landing page
2. `pages/landing.css` - Page-specific styles
3. `docs/landing-page-guide.md` - Documentation

## Quality Checks

- [ ] Semantic HTML structure
- [ ] Clear value proposition in hero
- [ ] Realistic, industry-appropriate content
- [ ] No Lorem Ipsum or placeholders
- [ ] All sections properly structured
- [ ] Responsive layout (mobile, tablet, desktop)
- [ ] WCAG AA contrast ratios
- [ ] Proper heading hierarchy (H1 → H2 → H3)
- [ ] CTAs prominent and action-oriented
- [ ] Social proof included
- [ ] Trust indicators present
- [ ] Footer complete
- [ ] Images have alt text
- [ ] Meta tags for SEO

## Example Usage

```
/mba-build-landing-page product_name="Acme Analytics Platform" industry="analytics" sections="hero,social-proof,features,pricing,faq,cta" theme="neutral" cta_text="Start Free Trial"
```

This will generate a complete landing page for an analytics SaaS product with neutral theme.

## Anti-Patterns to Avoid

Reference `.cursor/rules/80-anti-ai-patterns.mdc`:
- No generic "Lorem ipsum" text
- No "Click here" buttons
- No centered paragraphs
- No rainbow colors
- No excessive gradients
- No unrealistic data (all perfect numbers)
- No missing empty states
- No tiny touch targets on mobile

