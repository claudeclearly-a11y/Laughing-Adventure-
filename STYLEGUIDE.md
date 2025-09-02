# Combined Professional-Industrial-Emergency Style Guide

## Purpose
This style guide documents the color system, design tokens, and basic component patterns for the WordPress theme in this repository. It is mobile-first, accessible, and built to support block-based and PHP template integration.

## Palette (tokens)
- --color-navy: #2c3e50;  /* Headers, navigation, professional trust elements */
- --color-industrial-orange: #d35400; /* Primary CTAs, service highlights */
- --color-warm-orange: #e67e22; /* Hover states, secondary actions */
- --color-emergency-red: #e74c3c; /* Urgent/emergency messaging only */
- --color-golden: #f39c12; /* Pricing, special offers, accent */

Use these tokens in CSS variables, theme.json color palettes, and as source-of-truth tokens for block styles.

## Tokens (recommended)
- Colors: as above with semantic names
- Type scale (mobile-first):
  - --type-xxs: 12px
  - --type-xs: 14px
  - --type-sm: 16px
  - --type-md: 20px
  - --type-lg: 28px
  - --type-xl: 36px
- Spacing scale (8px base): .25x, .5x, 1x, 1.5x, 2x
  - --space-1: 8px
  - --space-2: 12px
  - --space-3: 16px
  - --space-4: 24px
  - --space-5: 32px

## Accessibility rules
- CTAs must meet contrast ratio >= 4.5:1 for normal text; for large text >= 3:1 is acceptable if bold and >=18pt.
- Emergency red (#e74c3c) use only for emergency banners and buttons. Also provide an alternative, darker outline/background when used on non-white contexts.
- All images must have meaningful alt text; decorative images should use empty alt (alt="").
- Forms must use <label for=> and have clear error messages.
- Focus states: visible 3px ring using a semi-transparent navy or golden accent.

## Typography
- System stack with Montserrat as a brand font (loaded via Google):
  font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
- Headings: use the type scale. H1 -> --type-xl, H2 -> --type-lg, H3 -> --type-md, body -> --type-sm.

## Buttons
- Primary (.btn--primary): background: var(--color-industrial-orange), color: #fff, border-radius: 6px, padding: var(--space-2) var(--space-3), font-weight:700.
- Primary hover: background: var(--color-warm-orange).
- Emergency (.btn--emergency): background: var(--color-emergency-red), color: #fff; reserved for emergency actions and banners.
- Outline (.btn--outline): border:2px solid var(--color-navy); background: transparent; color: var(--color-navy).

## Forms
- Inputs: 1px solid #d8d8d8; border-radius:6px; padding:10px; font-size: var(--type-sm).
- Error state: border-color: var(--color-emergency-red); icon + aria-invalid="true".

## Components
- Header: sticky, background: var(--color-navy) or brand red variant; include skip-to-content link, phone CTA as a pill.
- Hero: mobile-first stacked copy + CTA, optional card aside for quote form (in WP implement as a block or template-part).
- Services grid: dynamic block reading Services CPT.
- Testimonial list: horizontally scrollable on small screens; on desktop use grid.

## WordPress integration notes
- Add the palette to theme.json under "settings -> color -> palette" using the token names.
- Implement dynamic blocks for Services, Testimonials, and Brands. Store data in CPTs.
- Quote form: implement endpoint via register_rest_route. Use nonce verification and store submissions as CPT 'quote_request' or send to CRM.

## File references
- assets/css/_palette.css – CSS variables and small utility classes (generated from tokens).
- template-parts/hero.php – Use token classes and grid/layout helpers.

## Versioning and maintenance
- Update this guide when new tokens are added.
- Keep theme.json consistent with these tokens so blocks and PHP templates share the same design system.

---

> This style guide is mobile-first and designed to be used directly by theme developers and editors.
