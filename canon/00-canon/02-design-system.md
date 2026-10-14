<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE: fill me in via interview

## Goal of this file
The shared visual language: tokens, typography, spacing, accessibility floor,
forbidden patterns. Products copy the tokens into their own frontend code, so
this file is the source those copies are checked against.

## Interview prompts
1. "Does a product already have a design system, a tokens file, a Figma
   library? Share it." If several products have one, list where they differ
   and decide each difference before writing.
2. If starting fresh: three words for the feeling; core colors with hex
   values; domain color conventions (what red may and may not mean);
   typography; accessibility floor (WCAG level, contrast); motion rules.
3. "Which patterns are forbidden everywhere?" (raw IDs in the UI, color as
   the only signal, ...)

## Rules
- Every token has a name, a value and a usage. A token without a usage gets
  misused.
- Semantic colors carry a "never used for" line; for other tokens that
  column may stay empty.
- Tokens are physically copied into each product. A token change here needs a
  token change in every product that copied it; `04-process/sync-checklist.md`
  covers that.
- A product that needs a different value logs the exception in its own
  `01-products/<product>.md`, with the reason.

END BOOTSTRAP -->

# Design System

> Run `Bootstrap the canon` to fill in.

## Philosophy

## Color tokens

| Token | Value | Usage | Never used for |
|---|---|---|---|

## Typography

## Spacing and layout

## Accessibility floor

## Forbidden patterns

## Where products keep their copy

Each project's bootstrap drafts its own row here.

| Product | Tokens file | Last checked against this file |
|---|---|---|
