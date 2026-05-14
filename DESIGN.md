 ---
version: alpha
name: Linear
description: "A near-black product-focused marketing canvas built around #010102 (the deepest dark surface of any tool in this collection), light gray text (#f7f8f8), and the signature Linear lavender-blue (#5e6ad2) used as the single chromatic accent. The system reads as software-craft documentation: dense, technical, and quietly luxurious. Display type is set in the Linear custom sans (SF Pro Display fallback) at 500–700 with measured negative tracking. Cards live as charcoal panels (#0f1011) with hairline borders. The accent lavender appears on the brand mark, focus rings, and a few intentional CTAs — never decoratively."

colors:
  primary: "#5e6ad2"
  on-primary: "#ffffff"
  primary-hover: "#828fff"
  primary-focus: "#5e69d1"
  ink: "#f7f8f8"
  ink-muted: "#d0d6e0"
  ink-subtle: "#8a8f98"
  ink-tertiary: "#62666d"
  canvas: "#010102"
  surface-1: "#0f1011"
  surface-2: "#141516"
  surface-3: "#18191a"
  surface-4: "#191a1b"
  hairline: "#23252a"
  hairline-strong: "#34343a"
  hairline-tertiary: "#3e3e44"
  inverse-canvas: "#ffffff"
  inverse-surface-1: "#f5f6f6"
  inverse-ink: "#000000"
  brand-secure: "#7a7fad"
  semantic-success: "#27a644"

typography:
  display-xl:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 80px
    fontWeight: 600
    lineHeight: 1.05
    letterSpacing: -3.0px
  display-lg:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 56px
    fontWeight: 600
    lineHeight: 1.10
    letterSpacing: -1.8px
  display-md:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 40px
    fontWeight: 600
    lineHeight: 1.15
    letterSpacing: -1.0px
  headline:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 28px
    fontWeight: 600
    lineHeight: 1.20
    letterSpacing: -0.6px
  card-title:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 22px
    fontWeight: 500
    lineHeight: 1.25
    letterSpacing: -0.4px
  subhead:
    fontFamily: "SF Pro Display, -apple-system, system-ui, Inter, sans-serif"
    fontSize: 20px
    fontWeight: 400
    lineHeight: 1.40
    letterSpacing: -0.2px
  body-lg:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: -0.1px
  body:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: -0.05px
  body-sm:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  caption:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.40
    letterSpacing: 0
  button:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: 0
  eyebrow:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 13px
    fontWeight: 500
    lineHeight: 1.30
    letterSpacing: 0.4px
  mono:
    fontFamily: "JetBrains Mono, ui-monospace, SF Mono, Menlo, monospace"
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0

rounded:
  xs: 4px
  sm: 6px
  md: 8px
  lg: 12px
  xl: 16px
  xxl: 24px
  pill: 9999px
  full: 9999px

spacing:
  xxs: 4px
  xs: 8px
  sm: 12px
  md: 16px
  lg: 24px
  xl: 32px
  xxl: 48px
  section: 96px

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: "8px 14px"
  button-secondary:
    backgroundColor: "{colors.surface-1}"
    textColor: "{colors.ink}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: "8px 14px"
    borderColor: "{colors.hairline}"
  feature-card:
    backgroundColor: "{colors.surface-1}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.lg}"
    padding: "24px"
    borderColor: "{colors.hairline}"
  top-nav:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    height: 56px
  footer:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink-subtle}"
    typography: "{typography.caption}"
    padding: "64px 32px"
---

## Overview

Linear's marketing canvas is the deepest dark surface in this collection —
`{colors.canvas}` is `#010102`, essentially pure black with a faint blue tint. On
top sits a four-step surface ladder (`{colors.surface-1}` through
`{colors.surface-4}`) for cards, panels, and lifted tiles, with hairline borders.
Light gray text (`{colors.ink}` `#f7f8f8`) carries the body and headlines.

The single chromatic accent is **Linear lavender-blue** `{colors.primary}` (`#5e6ad2`)
— used on the brand mark, focus rings, and the primary CTA button. Linear avoids
saturated secondary colors on the marketing canvas entirely.

**Key Characteristics:**
- Dark-canvas system — `{colors.canvas}` (#010102) is the deepest dark in this collection
- Lavender-blue accent (`{colors.primary}` #5e6ad2) — used scarcely: brand mark, focus, primary CTA
- Four-step surface ladder (canvas → surface-1 → surface-2 → surface-3 → surface-4) carries hierarchy without shadow
- Display tracking pulls aggressively negative (-3.0px at 80px); body holds at -0.05px
- Cards use `{rounded.lg}` 12px corners with 1px hairline borders — never pill
- No atmospheric gradients. No spotlight cards. No second chromatic color

## Colors

### Brand & Accent
- **Lavender-Blue** (`{colors.primary}` — `#5e6ad2`): Signature accent — primary CTA, brand mark, link emphasis
- **Lavender Hover** (`{colors.primary-hover}` — `#828fff`): Hovered CTA state
- **Lavender Focus** (`{colors.primary-focus}` — `#5e69d1`): Focus rings

### Surface
- **Canvas** (`{colors.canvas}` — `#010102`): Default page background — near-pure black with faint blue tint
- **Surface 1** (`{colors.surface-1}` — `#0f1011`): Feature cards, pricing cards, screenshot panels
- **Surface 2** (`{colors.surface-2}` — `#141516`): Featured pricing card, hovered cards
- **Surface 3** (`{colors.surface-3}` — `#18191a`): Sub-nav, dropdowns
- **Hairline** (`{colors.hairline}` — `#23252a`): 1px borders on cards and dividers
- **Hairline Strong** (`{colors.hairline-strong}` — `#34343a`): Input focus rings

### Text
- **Ink** (`{colors.ink}` — `#f7f8f8`): All headlines and emphasized body type
- **Ink Muted** (`{colors.ink-muted}` — `#d0d6e0`): Secondary type — meta info on hero panels
- **Ink Subtle** (`{colors.ink-subtle}` — `#8a8f98`): Tertiary — footer columns, deselected tabs
- **Ink Tertiary** (`{colors.ink-tertiary}` — `#62666d`): Disabled, footnotes

## Typography

### Font Substitutes
Linear's custom faces are proprietary. Open-source substitutes:
- **Display/Body** — *Inter* (weight 400/500/600) is the closest match
- **Mono** — *JetBrains Mono* (weight 400) at 12–13px

### Hierarchy

| Token                     | Size | Weight | Letter Spacing | Use                                 |
| ------------------------- | ---- | ------ | -------------- | ----------------------------------- |
| `{typography.display-xl}` | 80px | 600    | -3.0px         | Largest hero headline               |
| `{typography.display-lg}` | 56px | 600    | -1.8px         | Section opener headlines            |
| `{typography.display-md}` | 40px | 600    | -1.0px         | Sub-section headlines               |
| `{typography.headline}`   | 28px | 600    | -0.6px         | CTA banner heading                  |
| `{typography.card-title}` | 22px | 500    | -0.4px         | Feature card title                  |
| `{typography.subhead}`    | 20px | 400    | -0.2px         | Lead body, intro paragraphs         |
| `{typography.body-lg}`    | 18px | 400    | -0.1px         | Hero subhead, lead paragraphs       |
| `{typography.body}`       | 16px | 400    | -0.05px        | Default body                        |
| `{typography.body-sm}`    | 14px | 400    | 0              | Card body, footer columns           |
| `{typography.caption}`    | 12px | 400    | 0              | Captions, meta, status              |
| `{typography.button}`     | 14px | 500    | 0              | All button labels                   |
| `{typography.eyebrow}`    | 13px | 500    | +0.4px         | Section eyebrow (positive tracking) |
| `{typography.mono}`       | 13px | 400    | 0              | Code in product screenshots         |

## Do's and Don'ts

### Do
- Reserve `{colors.canvas}` (#010102) as the system's anchor — the faint blue tint is intentional
- Use `{colors.primary}` lavender ONLY for: brand mark, primary CTA, focus ring, link emphasis
- Use the four-step surface ladder for hierarchy; avoid skipping levels
- Apply negative letter-spacing aggressively on display type
- Compose CTAs as `{rounded.md}` 8px corners — never pill-shaped

### Don't
- Don't ship a light-mode surface
- Don't use lavender as a section background or card fill
- Don't introduce a second chromatic accent
- Don't add atmospheric gradients or spotlight cards
- Don't use `#000000` true black as the canvas
- Don't combine multiple bright accents in product mockups
