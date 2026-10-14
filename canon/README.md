# <Organization> Canon

The single source of truth for what <Organization>'s products share: values, vision, design system, tone of voice, terminology, naming, writing style, and the development and release workflows. Each product repo references this repo instead of carrying, and slowly changing, its own copy.

## Why this exists

<Fill in after bootstrap: what made a canon necessary. The usual story: several products each wrote their own vision text, design principles and workflow notes. Nobody disagreed, but nothing made them check against each other, so the copies drifted apart. An audit found the differences; this repo is where the answers now live.>

## How a product repo uses this

Each product's own `CLAUDE.md` **points at** these files and doesn't restate them. Paste this block at the top of every product's `CLAUDE.md`:

```markdown
## Canon Alignment
Foundational values, vision, design system, and naming rules live in `../<org>-canon`
(not duplicated here). Check:
- `00-canon/01-values-and-vision.md`: at idea intake
- `00-canon/02-design-system.md` + `03-ux-principles.md`: at feature and design review
- `00-canon/04-tone-of-voice.md` + `07-writing-style-guide.md`: when writing user-facing copy
- `00-canon/05-terminology.md` + `06-naming-conventions.md`: when naming anything
The development workflow below follows `00-canon/08-development-workflow.md`;
releases follow `00-canon/09-release-workflow.md`.
This product's own adaptations are logged in `<org>-canon/01-products/<this-product>.md`.
```

References use a relative path (`../<org>-canon`), so all repos are cloned as siblings under one parent directory.

## Structure

```
<org>-canon/
├── README.md                    this file
├── CLAUDE.md                    working rules for every Claude session here
├── 00-canon/                    what every product shares
│   ├── 01-values-and-vision.md
│   ├── 02-design-system.md
│   ├── 03-ux-principles.md
│   ├── 04-tone-of-voice.md
│   ├── 05-terminology.md        cross-product terms only
│   ├── 06-naming-conventions.md
│   ├── 07-writing-style-guide.md
│   ├── 08-development-workflow.md
│   └── 09-release-workflow.md
├── 01-products/                 one page per product: deliberate adaptations, drift log
│   └── _template.md
├── 02-roadmap/
│   └── portfolio-roadmap.md     priorities, snapshot, cross-product dependencies, log
├── 03-conflicts/
│   └── conflict-log.md          every conflict found, how it was decided, where it landed
├── 04-process/
│   ├── proposing-a-change.md    how canon changes
│   ├── sync-checklist.md        the follow-through after a change
│   └── extracting-a-canon.md    building a canon from repos that already exist
└── 05-business/                 optional: open business threads with their reasoning
    └── open-discussions.md
```

## The three layers of truth

| Layer | Lives in | Changes how |
|---|---|---|
| What all products share | `00-canon/` | Through `04-process/proposing-a-change.md`; the decision owner decides |
| How one product differs, on purpose | `01-products/<product>.md` | Logged with a reason whenever a product deviates |
| How one product is built | The product repo's own `CLAUDE.md` and `docs/` | Through that product's six-phase workflow |

A product can deviate from canon. It can't do so silently: a deviation without a line in its product page is drift, and drift gets fixed.

## Status

<Fill in after bootstrap: which files are written, which products are connected, when each was last re-checked.>
