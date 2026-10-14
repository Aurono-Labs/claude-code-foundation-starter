<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

CANON MODE: if this project connects to a canon repo, don't run this
interview. Replace this whole file with a pointer to
`../<org>-canon/00-canon/02-design-system.md`, followed by a table of this
product's deliberate exceptions (token, canon value, this product's value,
reason). Record the same exceptions in the canon's product page draft.

## Goal of this file
Lock the visual and accessibility rules of the product so they survive across
designers, contributors, and sessions. The frontend equivalent of
domain_terminology.md.

## Interview prompts

1. "Do you have an existing design system, brand guidelines, Figma library,
   or a UI screenshot of the current product? Share it — I'll extract
   tokens and conventions."

2. If starting fresh:

   a) "What feeling should the product evoke? Three words. Examples:
      'calm, confident, personal' or 'precise, technical, fast' or
      'warm, trustworthy, accessible'."

   b) "What are the three to five core colors? Background, foreground,
      accent, semantic positive/negative/warning. Hex values."

   c) "Are there color conventions specific to your domain? Examples
      in finance: 'red is for system errors only, not market losses'.
      In healthcare: 'red is for critical only, not warnings'."

   d) "What's the typography? One sans, one mono, sizes."

   e) "What's the accessibility floor? WCAG 2.1 AA at minimum?
      Color contrast targets?"

   f) "Any motion / animation conventions? Reduced-motion respect?"

3. "What anti-patterns are forbidden? E.g. 'never use raw UUIDs in user-
   facing UI', 'never show technical event names outside debug layers'."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Design System

## Design Philosophy
<short paragraph on the feeling and target user>

## Color Tokens
### Surface
| Token | Hex | Usage |
|---|---|---|
| surface-base | #... | Page background |
| surface-raised | #... | Cards, modals |

### Accent
### Text
### Semantic
### Domain-specific (if any — e.g. positive/negative for finance)

## Typography
| Token | Family | Size | Weight | Usage |

## Spacing & Layout
<grid, breakpoints, density>

## Accessibility Floor
- WCAG 2.1 AA target
- Contrast ratios
- Focus visibility
- Keyboard navigation
- Reduced motion

## Forbidden Patterns
- <pattern> — <reason>
```

## Rules

- Every token has a name, a hex, AND a usage. A token without usage gets
  misused.
- Semantic colors have a "never used for X" line. Red specifically.
- Accessibility floor is not aspirational — it's the minimum that ships.
- This file is referenced by every UI feature in Phase 3 (Planning) and
  Phase 4 (Execution).

## Example — how Aurono Labs answered this

> ### Design philosophy
> Light-mode-first, designed for a Raspberry Pi 5 at 1080p, responsive to
> 768px. Warm Stone gray palette + Teal accent — trust + approachability.
> Information density, glanceable status, low cognitive load.
>
> ### Color tokens (excerpt)
> | Token | Hex | Usage |
> |---|---|---|
> | `surface-base` | `#FAFAF9` (Stone-50) | Page background |
> | `surface-raised` | `#FFFFFF` | Sidebar, cards, modals |
> | `accent-primary` | `#0D9488` (Teal-600) | Primary actions, active nav |
> | `text-primary` | `#1C1917` (Stone-900) | Headings, primary content |
> | `loss-text` | `#9B6549` (Burnt sienna) | P&L losses — warm, not alarming |
> | `negative` | `#DC2626` (Red-600) | **System errors only — never market losses** |
>
> ### Core principle
> **Red means broken. Warm tones mean "the market moved."** Reserve red
> exclusively for system errors, validation failures, and things the user
> needs to fix.
>
> ### Multi-channel encoding
> Color is never the sole indicator. Every value uses at least two channels:
> color (teal/sienna) + shape (▲/▼) + text (+/− sign) + label.
>
> ### Accessibility floor
> WCAG 2.1 AA. 4.5:1 text contrast, 3:1 UI elements, focus visible (2px ring),
> keyboard navigable, semantic HTML, respect `prefers-reduced-motion`.

Source: Aurono Start (reference implementation by Aurono Labs · auronolabs.com) · `docs/design/DESIGN-SYSTEM.md`.

END BOOTSTRAP -->

# Design System

> Run `Bootstrap the foundation` to fill in.

<!-- Design system sections go here -->
