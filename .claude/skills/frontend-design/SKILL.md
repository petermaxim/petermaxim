---
name: frontend-design
description: "Generates creative, polished frontend interfaces that avoid generic AI aesthetics. Commits to a bold aesthetic direction—brutalist, editorial, luxury, retro-futuristic, organic—before writing a single line of code. Distinctive typography (never Arial/Inter/Roboto), constrained color palettes, micro-interactions on every hover/focus, skeleton loading states. Use when building landing pages, dashboards, marketing sites, or any UI that needs to look intentional and memorable."
user-invocable: true
---

# Frontend Design Excellence

Generate distinctive, production-grade frontend interfaces. The goal is thoughtful design intentionality—not generic AI output.

## Before Writing Any Code

Establish a clear aesthetic direction by answering:
1. What problem does this interface solve?
2. What emotional tone suits the product and audience?
3. What technical constraints exist?
4. What would make this interface unforgettable?

Pick ONE bold direction and execute it with precision. Bold maximalism and refined minimalism both work—the key is intentionality, not intensity.

## Typography

- Choose fonts that are beautiful, unique, and interesting
- Avoid generic fonts: Arial, Inter, Roboto, Helvetica, system-ui
- Favor characterful, unexpected typefaces that elevate the aesthetic
- Pair a display font with a complementary body typeface
- Load via Google Fonts or Bunny Fonts CDN

## Color System

- Constrained palette: 1 primary + 1 accent + neutrals (never more than 5 total)
- Define as CSS custom properties on `:root`
- Semantic naming: `--color-brand`, `--color-accent`, `--color-surface`, `--color-text`
- Test contrast ratios—4.5:1 minimum for body text

## Layout & Composition

- Reject predictable grid layouts; embrace asymmetry, overlap, diagonal flow
- Use generous whitespace as a design element
- Layer elements—cards that bleed, text that overlaps imagery
- Unexpected spatial relationships create visual tension and interest

## Motion & Animation

- One well-orchestrated page load with staggered reveals
- Micro-interactions on every interactive element (hover, focus, active)
- CSS transitions for simple state changes; keyframes for sequences
- No spinners—use skeleton loading states that match content shape
- Respect `prefers-reduced-motion`

## Aesthetics to Avoid

Never produce:
- Generic AI-generated layouts (equal-width cards, centered hero, stock imagery slots)
- Overused font families (Inter, Roboto, Arial)
- Clichéd color schemes (blue/white SaaS, dark-mode-with-purple-accents)
- Cookie-cutter components that lack context-specific character
- Predictable section order (hero → features → pricing → CTA)

## Implementation Guidance

- Use CSS custom properties for the entire design system
- Write semantic HTML—accessibility is non-negotiable
- Mobile-first responsive design
- Complexity should match the aesthetic vision: maximalist designs warrant elaborate animations; minimalist work demands precise restraint
- Every hover state, every focus ring, every active state should feel considered

## Examples by Aesthetic Direction

**Brutalist**: raw typography, visible structure, high contrast, no decorative chrome
**Editorial**: magazine-style layout, large display type, photo-forward, unexpected crops
**Luxury**: generous whitespace, serif typography, muted palette, refined micro-animations
**Retro-futuristic**: scanlines, terminal fonts, neon accents, grid overlays
**Organic**: irregular shapes, nature-inspired palette, fluid animations, textured surfaces
