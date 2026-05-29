---
name: ui-ux-pro-max
description: "UI/UX design intelligence for web and mobile. Includes 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, and HTML/CSS). Actions: plan, build, create, design, implement, review, fix, improve, optimize, enhance, refactor, and check UI/UX code. Projects: website, landing page, dashboard, admin panel, e-commerce, SaaS, portfolio, blog, and mobile app. Elements: button, modal, navbar, sidebar, card, table, form, and chart. Styles: glassmorphism, claymorphism, minimalism, brutalism, neumorphism, bento grid, dark mode, responsive, skeuomorphism, and flat design. Topics: color systems, accessibility, animation, layout, typography, font pairing, spacing, interaction states, shadow, and gradient."
user-invocable: true
---

# UI/UX Pro Max

Comprehensive design guidance across 10 technology stacks with 50+ distinct visual styles, 161 color palettes, 57 font pairings, and 99 UX guidelines.

## When to Apply

**Must Use:** designing new pages, creating/refactoring UI components, choosing color/typography systems, reviewing UI code for accessibility, implementing responsive behavior, making product-level design decisions, improving interface quality

**Skip:** pure backend logic, API design only, performance optimization unrelated to visuals, infrastructure work, non-visual scripts

Invoke this skill when tasks affect how features **look, feel, move, or are interacted with**.

## Priority Rule Categories (1–10)

| Priority | Category | Impact | Key Focus |
|----------|----------|--------|-----------|
| 1 | Accessibility | CRITICAL | Contrast 4.5:1 minimum, keyboard navigation, descriptive labels |
| 2 | Touch & Interaction | CRITICAL | 44×44px minimum targets, 8px+ spacing, loading feedback |
| 3 | Performance | HIGH | WebP/AVIF images, lazy loading, cumulative layout shift <0.1 |
| 4 | Style Selection | HIGH | Match product type, maintain consistency, use SVG icons |
| 5 | Layout & Responsive | HIGH | Mobile-first design, viewport meta, no horizontal scroll |
| 6 | Typography & Color | MEDIUM | 16px base size, 1.5+ line-height, semantic color tokens |
| 7 | Animation | MEDIUM | 150–300ms duration, transform/opacity only, respect reduced-motion |
| 8 | Forms & Feedback | MEDIUM | Visible labels, errors near fields, progressive disclosure |
| 9 | Navigation Patterns | HIGH | Predictable back behavior, deep linking, max 5 bottom items |
| 10 | Charts & Data | LOW | Match chart type to data, use accessible colors, show legends |

## Quick Reference Highlights

### Accessibility (CRITICAL)

- 4.5:1 contrast minimum for normal text, 3:1 for large text (WCAG)
- Visible focus rings on interactive elements (2–4px)
- Descriptive alt text for meaningful images
- Keyboard navigation with logical tab order
- aria-labels for icon-only buttons

### Touch & Interaction (CRITICAL)

- 44×44pt minimum touch target (Apple) / 48×48dp (Material)
- 8px minimum gap between touch targets
- No hover-only interactions
- Visual feedback within 100ms of tap
- Clear loading states during async operations

### Performance (HIGH)

- WebP/AVIF with responsive images (srcset/sizes)
- Lazy loading for non-critical assets
- Declare width/height or aspect-ratio to prevent layout shift
- font-display: swap/optional
- Per-frame work under ~16ms for 60fps

### Style Selection (HIGH)

- Match style to product type (glassmorphism, minimalism, brutalism, neumorphism, etc.)
- Consistency across all pages
- SVG icons instead of emojis
- Shadows and effects aligned with chosen style
- Respect platform idioms (iOS HIG vs Material Design)

### Layout & Responsive (HIGH)

- Mobile-first design approach
- Systematic breakpoints (375/768/1024/1440)
- 16px minimum body text on mobile
- Readable line length (35–60 chars mobile, 60–75 desktop)
- No horizontal scroll
- 4pt/8dp spacing increments

### Typography & Color (MEDIUM)

- 1.5–1.75 line-height for body text
- Limit lines to 65–75 characters
- Consistent type scale (12/14/16/18/24/32)
- Semantic color tokens not raw hex
- Test dark mode contrast separately from light mode

### Animation (MEDIUM)

- Micro-interactions: 150–300ms
- Use transform/opacity only (avoid animating width/height)
- Skeleton screens for operations >300ms
- Interruptible animations
- Respect prefers-reduced-motion system preference

### Forms & Feedback (MEDIUM)

- Visible labels (never placeholder-only)
- Errors below related fields
- Helper text below complex inputs
- Inline validation on blur
- Allow undo for destructive actions
- Auto-save drafts in long forms

### Navigation Patterns (HIGH)

- Bottom navigation: maximum 5 items with labels
- Back navigation restores scroll position and state
- Deep linking for all key screens
- Platform-standard gestures (iOS swipe-back, Android predictive back)
- Consistent navigation placement across pages

### Charts & Data (LOW)

- Match chart type to data (line for trends, bar for comparison, pie for proportion)
- Accessible color palettes (not red/green only)
- Table alternative for screen readers
- Legends and tooltips
- Responsive chart reflow on small screens

## Icons & Visual Elements

| Rule | Do | Avoid |
|------|----|----|
| Icon source | Use vector icons (Lucide, SVG) | Emojis for navigation/system controls |
| Asset format | SVG for clean scaling and theming | Raster PNG icons |
| Sizing | Define icon sizes as tokens (icon-sm, icon-md=24pt) | Arbitrary mixed values |
| Touch targets | Minimum 44×44pt interactive area | Small icons without expanded tap area |
| Contrast | 4.5:1 for small elements, 3:1 minimum for UI glyphs | Low-contrast icons |

## Light/Dark Mode Contrast

| Rule | Do | Don't |
|------|----|----|
| Surface separation | Clear card/surface distinction with opacity/elevation | Overly transparent surfaces |
| Light text contrast | Body text ≥4.5:1 against light surfaces | Low-contrast gray body text |
| Dark text contrast | Primary ≥4.5:1, secondary ≥3:1 on dark surfaces | Text blending into background |
| Token-driven theming | Semantic color tokens mapped per theme | Hardcoded per-screen hex values |
| Scrim strength | Modal scrim 40–60% black | Weak scrim leaving background competing |

## Pre-Delivery Checklist

### Visual Quality
- [ ] No emoji icons (use SVG instead)
- [ ] Consistent icon family and style throughout
- [ ] Pressed states don't shift layout or cause jitter
- [ ] Semantic theme tokens used consistently

### Interaction
- [ ] All tappable elements provide clear pressed feedback
- [ ] Touch targets ≥44×44pt iOS, ≥48×48dp Android
- [ ] Micro-interactions 150–300ms with native easing
- [ ] Disabled states visually clear and non-interactive
- [ ] Screen reader focus order matches visual order

### Light/Dark Mode
- [ ] Primary text ≥4.5:1 contrast in both themes
- [ ] Secondary text ≥3:1 contrast in both themes
- [ ] Both themes tested before delivery

### Layout
- [ ] Safe areas respected for fixed UI
- [ ] Scroll content visible (not behind fixed bars)
- [ ] Tested on small phone, large phone, tablet (portrait/landscape)
- [ ] 4/8dp spacing rhythm maintained

### Accessibility
- [ ] Meaningful images and icons have labels
- [ ] Form fields have labels, hints, error messages
- [ ] Color not the only indicator
- [ ] Reduced motion and dynamic text size supported
