---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, artifacts, posters, or applications (examples include websites, landing pages, dashboards, React components, HTML/CSS layouts, or when styling/beautifying any web UI). Generates creative, polished code and UI design that avoids generic AI aesthetics.
license: Complete terms in LICENSE.txt
---

# Frontend Design

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design Thinking

Before coding, understand the context and commit to a BOLD aesthetic direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, etc. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work — the key is intentionality, not intensity.

Then implement working code (HTML/CSS/JS, React, Vue, etc.) that is:
- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail

---

## Frontend Aesthetics Guidelines

### Typography

Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics — unexpected, characterful font choices. Pair a distinctive display font with a refined body font.

```css
/* ❌ Generic (AI slop) */
font-family: Inter, system-ui, sans-serif;
font-family: Roboto, Arial, sans-serif;
font-family: -apple-system, BlinkMacSystemFont, system-ui;

/* ✅ Distinctive */
font-family: 'Playfair Display', Georgia, serif;
font-family: 'Space Mono', 'Courier New', monospace;
font-family: 'Fraunces', 'Palatino Linotype', serif;
```

Load fonts from Google Fonts or Bunny Fonts:
```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;900&family=Instrument+Sans:wght@400;500&display=swap" rel="stylesheet">
```

### Color & Theme

Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.

```css
:root {
  /* ❌ Generic (boring) */
  --primary: #6366f1; /* Same purple everyone uses */
  
  /* ✅ Distinctive (editorial dark) */
  --bg: #0A0A07;
  --surface: #111110;
  --ink: #F0EDE6;
  --accent: #D4A843; /* Warm gold, not cold blue/purple */
}
```

**Anti-slop rule:** Never default to purple gradients on white, blue-to-purple color schemes, or any "SaaS starter" palette. Make a genuine creative choice.

### Motion

Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Focus on high-impact moments: one well-orchestrated page load with staggered reveals creates more delight than scattered micro-interactions.

```css
/* ✅ Staggered entrance animation */
.hero-title { animation: fadeUp 0.6s ease-out both; }
.hero-sub   { animation: fadeUp 0.6s ease-out 0.15s both; }
.hero-cta   { animation: fadeUp 0.6s ease-out 0.3s both; }

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Respect reduced motion */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; }
}
```

### Spatial Composition

Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density — but never the default centered column.

```css
/* ❌ Default (boring) */
.container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }

/* ✅ Intentional composition */
.hero {
  display: grid;
  grid-template-columns: 1fr 1.618fr; /* Golden ratio */
  gap: 0;
  min-height: 100svh;
}
.hero-text { padding: 15vw 5vw 10vw 8vw; }
.hero-visual { overflow: hidden; position: relative; }
```

### Backgrounds & Visual Depth

Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures.

```css
/* ✅ Noise texture overlay */
.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,..."); /* SVG noise */
  opacity: 0.04;
  pointer-events: none;
}

/* ✅ Gradient mesh */
.hero {
  background: 
    radial-gradient(ellipse at 20% 50%, rgba(212, 168, 67, 0.15) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 20%, rgba(180, 80, 60, 0.1) 0%, transparent 50%),
    #0A0A07;
}
```

---

## Anti-Slop Blacklist

**NEVER use** these patterns — they scream "AI-generated":

1. **Purple/violet/indigo gradient backgrounds** or blue-to-purple color schemes
2. **The 3-column feature grid**: icon-in-colored-circle + bold title + 2-line description, repeated 3×
3. **Icons in colored circles** as section decoration
4. **Centered everything** (`text-align: center` on all headings, descriptions, cards)
5. **Uniform bubbly border-radius** (same large radius on every element)
6. **Decorative blobs**, floating circles, wavy SVG dividers
7. **Emoji as design elements** (rockets in headings, emoji as bullet points)
8. **Colored left-border on cards** (`border-left: 3px solid <accent>`)
9. **Generic hero copy** ("Welcome to [X]", "Unlock the power of...", "Your all-in-one solution for...")
10. **Cookie-cutter section rhythm** (hero → 3 features → testimonials → pricing → CTA, every section same height)
11. **Inter/Roboto/Arial/system-ui as primary display font** — the "I gave up on typography" signal

---

## Implementation Principles

### Match complexity to vision

- **Maximalist designs** need elaborate code with extensive animations and effects
- **Minimalist designs** need restraint, precision, and careful attention to spacing, typography, and subtle details
- Elegance comes from executing the vision well, not from adding features

### CSS architecture for bespoke designs

```css
/* Use CSS custom properties for the design system */
:root {
  /* Derived from the aesthetic direction */
  --font-display: 'Fraunces', serif;
  --font-body: 'Instrument Sans', sans-serif;
  
  --color-bg: #0C0C0A;
  --color-surface: #141412;
  --color-border: rgba(255,255,255,0.08);
  --color-ink: #F5F2EC;
  --color-ink-muted: #9A9589;
  --color-accent: #C8A96E;
  
  --radius-card: 2px;    /* Deliberately sharp for editorial look */
  --radius-button: 4px;
  
  --space-section: clamp(64px, 10vw, 128px);
}
```

### Performance considerations

```html
<!-- Preload critical fonts -->
<link rel="preload" href="/fonts/display.woff2" as="font" type="font/woff2" crossorigin>

<!-- Prevent flash of invisible text -->
<style>
  @font-face {
    font-family: 'Custom Display';
    src: url('/fonts/display.woff2') format('woff2');
    font-display: swap;
  }
</style>
```

### Accessibility without compromising aesthetics

```css
/* High-contrast focus that matches the design */
:focus-visible {
  outline: 2px solid var(--color-accent);
  outline-offset: 3px;
}

/* Don't remove focus for keyboard users */
:focus:not(:focus-visible) {
  outline: none;
}
```

---

## Design Inspiration Sources

- **Editorial**: Kinfolk magazine, Pin-Up architecture journal, eye magazine
- **Brutalist web**: Brutalistwebsites.com
- **Luxury**: Bottega Veneta, Loewe, Aesop brand sites
- **Tech-minimalist**: Linear.app, Vercel, Raycast
- **Experimental**: Awwwards showcase, Typewolf font pairings

Push boundaries. Show what is truly achievable when thinking outside the box and committing fully to a distinctive vision.
