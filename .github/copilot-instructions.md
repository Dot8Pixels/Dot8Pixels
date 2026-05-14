# Dot8Pixels — Frontend Agent Instructions

This repository is the personal portfolio for **Napat Sri-ampun (Dot8Pixels)**.
All frontend work must adhere to the **Linear design system** defined in [`DESIGN.md`](../DESIGN.md).

---

## Identity

| Field    | Value                        |
| -------- | ---------------------------- |
| Name     | Napat Sri-ampun              |
| Handle   | Dot8Pixels                   |
| Role     | Python Developer             |
| Focus    | Financial Systems · Data Analytics · LLM Applications |
| Email    | napatsriz@gmail.com          |
| LinkedIn | linkedin.com/in/napat-sri-ampun |
| GitHub   | github.com/Dot8Pixels         |

---

## Design Constraints (non-negotiable)

- Canvas is always `#010102` — never true `#000000`
- **Single chromatic accent** `#5e6ad2` (lavender-blue) — restrict to: brand mark, primary CTA, focus rings, link emphasis only
- **No light mode** — this is a dark-canvas–only system
- **No atmospheric gradients**, no spotlight card effects
- **No second chromatic accent**
- Cards use `border-radius: 12px` (--radius-lg) with a 1 px hairline border — never pill-shaped
- Display type carries aggressive negative tracking (−3.0 px at 80 px); body holds at −0.05 px

---

## CSS Custom Properties

Every frontend file must open with, or import, these tokens:

```css
:root {
  /* Brand */
  --color-primary:       #5e6ad2;
  --color-primary-hover: #828fff;
  --color-primary-focus: #5e69d1;
  --color-on-primary:    #ffffff;

  /* Surfaces (canvas → surface-4, darkest → slightly lifted) */
  --color-canvas:    #010102;
  --color-surface-1: #0f1011;
  --color-surface-2: #141516;
  --color-surface-3: #18191a;
  --color-surface-4: #191a1b;

  /* Hairlines */
  --color-hairline:          #23252a;
  --color-hairline-strong:   #34343a;
  --color-hairline-tertiary: #3e3e44;

  /* Text */
  --color-ink:          #f7f8f8;
  --color-ink-muted:    #d0d6e0;
  --color-ink-subtle:   #8a8f98;
  --color-ink-tertiary: #62666d;

  /* Border radius */
  --radius-xs:  4px;
  --radius-sm:  6px;
  --radius-md:  8px;
  --radius-lg:  12px;
  --radius-xl:  16px;
  --radius-xxl: 24px;

  /* Spacing */
  --space-xxs:     4px;
  --space-xs:      8px;
  --space-sm:      12px;
  --space-md:      16px;
  --space-lg:      24px;
  --space-xl:      32px;
  --space-xxl:     48px;
  --space-section: 96px;

  /* Typefaces */
  --font-display: "SF Pro Display", -apple-system, system-ui, Inter, sans-serif;
  --font-body:    Inter, system-ui, sans-serif;
  --font-mono:    "JetBrains Mono", ui-monospace, "SF Mono", Menlo, monospace;
}
```

---

## Typography Scale

| Token        | Size (px)        | Weight | Letter-spacing | Usage                      |
| ------------ | ---------------- | ------ | -------------- | -------------------------- |
| display-xl   | 80 (clamp 48–80) | 600    | −3.0 px        | Hero headline              |
| display-lg   | 56               | 600    | −1.8 px        | Section opener             |
| display-md   | 40 (clamp 28–40) | 600    | −1.0 px        | Sub-section headline       |
| headline     | 28               | 600    | −0.6 px        | CTA banner heading         |
| card-title   | 22               | 500    | −0.4 px        | Feature card title         |
| subhead      | 20               | 400    | −0.2 px        | Lead body / intro para     |
| body-lg      | 18               | 400    | −0.1 px        | Hero sub-head              |
| body         | 16               | 400    | −0.05 px       | Default body               |
| body-sm      | 14               | 400    | 0              | Card body, footer columns  |
| caption      | 12               | 400    | 0              | Meta, status               |
| button       | 14               | 500    | 0              | All button labels          |
| eyebrow      | 13               | 500    | +0.4 px        | Section eyebrow (ALLCAPS)  |
| mono         | 13               | 400    | 0              | Code, tech chips           |

---

## Component Patterns

### Button — Primary
```css
.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-on-primary);
  font-size: 14px; font-weight: 500;
  padding: 8px 14px;
  border-radius: var(--radius-md);
  border: none;
}
.btn-primary:hover  { background-color: var(--color-primary-hover); }
.btn-primary:focus-visible { outline: 2px solid var(--color-primary-focus); outline-offset: 2px; }
```

### Button — Secondary
```css
.btn-secondary {
  background-color: var(--color-surface-1);
  color: var(--color-ink);
  border: 1px solid var(--color-hairline);
  font-size: 14px; font-weight: 500;
  padding: 8px 14px;
  border-radius: var(--radius-md);
}
.btn-secondary:hover { background-color: var(--color-surface-2); border-color: var(--color-hairline-strong); }
```

### Feature Card
```css
.card {
  background-color: var(--color-surface-1);
  border: 1px solid var(--color-hairline);
  border-radius: var(--radius-lg);
  padding: var(--space-lg);
}
.card:hover { background-color: var(--color-surface-2); border-color: var(--color-hairline-strong); }
```

### Top Navigation
- Height: `56px`
- Background: `var(--color-canvas)` + bottom hairline border
- Nav link font: `body-sm` (14 px / 400)
- Brand: `body-sm` (14 px / 500) — accent dot in `var(--color-primary)`

### Eyebrow
```css
.eyebrow {
  font-size: 13px; font-weight: 500;
  letter-spacing: 0.4px;
  text-transform: uppercase;
  color: var(--color-primary);
}
```

---

## Layout Rules

- Content max-width: `1100 px`, centered
- Section vertical padding: `var(--space-section)` = 96 px
- Use CSS Grid / Flexbox — **no CSS frameworks** unless explicitly requested
- Mobile-first, single breakpoint at `768 px`: stack all columns, hide nav links

---

## Accessibility

- All interactive elements need `:focus-visible` rings: `outline: 2px solid var(--color-primary-focus); outline-offset: 2px;`
- Primary text on canvas (`#010102`) must use `var(--color-ink)` (#f7f8f8) — WCAG AA compliant
- Semantic HTML5: `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- External links: `target="_blank" rel="noopener noreferrer"`

---

## File Conventions

| File         | Purpose                         |
| ------------ | ------------------------------- |
| `index.html` | Portfolio landing page          |
| `styles.css` | Single stylesheet, token-driven |
| `DESIGN.md`  | Source of truth for all tokens  |

Do not introduce a CSS framework, build step, or JS bundler unless explicitly requested.
