<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE: fill me in via interview

CANON MODE: if this project connects to a canon repo, don't run this
interview. Replace this whole file with a pointer to
`../<org>-canon/00-canon/02-design-system.md`, followed by:
- where this project keeps its copy of the tokens (the file path);
- a table of this project's deliberate exceptions (token, canon value, this
  project's value, reason).
Ask for both. Record the exceptions in the canon's product page draft, and the
tokens path in the canon design system's "Where products keep their copy"
table (draft only, not committed).

## Goal of this file
Lock the visual and accessibility rules of the product so they survive across
designers, contributors, and sessions. The frontend equivalent of
domain_terminology.md.

## Interview prompts

1. "Do you have an existing design system, brand guidelines, Figma library,
   or a UI screenshot of the current product? Share it and I'll extract
   tokens and conventions."

2. If starting fresh:

   a) "What feeling should the product evoke? Three words. Examples:
      'calm, confident, personal' or 'precise, technical, fast' or
      'warm, trustworthy, accessible'."

   b) "What are the three to five core colors? Background, foreground,
      accent, semantic positive/negative/warning. Hex values."

   c) "Are there color conventions specific to your domain? Examples:
      'red is for errors only, never for a normal outcome the user dislikes'.
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
### Domain-specific (if any, e.g. status colors your domain gives a meaning)

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
- <pattern>: <reason>
```

## Rules

- Every token has a name, a hex, AND a usage. A token without usage gets
  misused.
- Semantic colors have a "never used for X" line. Red specifically.
- Accessibility floor is not aspirational; it's the minimum that ships.
- This file is referenced by every UI feature in Phase 3 (Planning) and
  Phase 4 (Execution).

END BOOTSTRAP -->

# Design System

> Run `Bootstrap the project` to fill in.

<!-- Design system sections go here -->
