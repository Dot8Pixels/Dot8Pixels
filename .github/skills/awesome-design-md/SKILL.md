---
name: awesome-design-md
description: 'Fetch and apply a DESIGN.md brand design system from the VoltAgent/awesome-design-md collection. Use when the user wants to style their project like a specific brand (e.g. Vercel, Stripe, Linear, Apple), generate consistent UI matching a known brand, or drop a DESIGN.md into the project root for AI agents to reference.'
argument-hint: 'Brand name (e.g. vercel, stripe, linear, apple, supabase)'
---

# Awesome DESIGN.md

A curated collection of DESIGN.md files extracted from 70+ real websites. Each file encodes a brand's complete design system — colors, typography, spacing, components, elevation, and responsive rules — in plain Markdown that AI agents read natively.

## When to Use

- User says "make it look like [brand]" or "use [brand]'s design system"
- User wants to drop a DESIGN.md into their project root
- User wants pixel-accurate UI matching a known brand's visual language
- User is using Google Stitch or any AI coding agent that reads DESIGN.md

## Available Brands

### AI & LLM Platforms
`claude` · `cohere` · `elevenlabs` · `minimax` · `mistral.ai` · `ollama` · `opencode.ai` · `replicate` · `runwayml` · `together.ai` · `voltagent` · `x.ai`

### Developer Tools & IDEs
`cursor` · `expo` · `lovable` · `raycast` · `superhuman` · `vercel` · `warp`

### Backend, Database & DevOps
`clickhouse` · `composio` · `hashicorp` · `mongodb` · `posthog` · `sanity` · `sentry` · `supabase`

### Productivity & SaaS
`cal` · `intercom` · `linear.app` · `mintlify` · `notion` · `resend` · `zapier`

### Design & Creative Tools
`airtable` · `clay` · `figma` · `framer` · `miro` · `webflow`

### Fintech & Crypto
`binance` · `coinbase` · `kraken` · `mastercard` · `revolut` · `stripe` · `wise`

### E-commerce & Retail
`airbnb` · `meta` · `nike` · `shopify` · `starbucks`

### Media & Consumer Tech
`apple` · `hp` · `ibm` · `nvidia` · `pinterest` · `playstation` · `spacex` · `spotify` · `theverge` · `uber` · `vodafone` · `wired`

### Automotive
`bmw` · `bmw-m` · `bugatti` · `ferrari` · `lamborghini` · `renault` · `tesla`

## Procedure

1. **Identify the brand** from the user's request or the argument hint. Match to a slug from the list above.
2. **Fetch the DESIGN.md** from the raw GitHub URL:
   ```
   https://raw.githubusercontent.com/VoltAgent/awesome-design-md/main/design-md/<slug>/DESIGN.md
   ```
3. **Save the file** to the project root as `DESIGN.md`.
4. **Confirm** to the user and briefly describe the brand's visual character (colors, typography mood).

## DESIGN.md Format

Each file follows the [Google Stitch DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/format/) with these sections:

| Section | Contents |
|---|---|
| Visual Theme & Atmosphere | Mood, density, design philosophy |
| Color Palette & Roles | Semantic name + hex + functional role |
| Typography Rules | Font families, full hierarchy table |
| Component Stylings | Buttons, cards, inputs, navigation with states |
| Layout Principles | Spacing scale, grid, whitespace philosophy |
| Depth & Elevation | Shadow system, surface hierarchy |
| Do's and Don'ts | Design guardrails and anti-patterns |
| Responsive Behavior | Breakpoints, touch targets, collapsing strategy |
| Agent Prompt Guide | Quick color reference, ready-to-use prompts |

The file ends with a YAML front-matter token block (`colors`, `typography`, `rounded`, `spacing`, `components`) for programmatic use.

## Usage After Installation

Once `DESIGN.md` is in the project root, tell the agent:
- "Build a landing page following DESIGN.md"
- "Create a pricing card using the design system in DESIGN.md"
- "Make this component match the style in DESIGN.md"

## Source

GitHub: https://github.com/VoltAgent/awesome-design-md  
Request a custom DESIGN.md: https://getdesign.md/request
