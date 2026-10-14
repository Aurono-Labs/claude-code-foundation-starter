# Extracting a Canon

For an organization that already has two or more product repos, each with its own vision text, design notes and workflow. Run this instead of the blank-page interview: it starts from what the products already say.

**Trigger:** "Extract a canon", or `Bootstrap the canon` when product repos already exist.

## When it's time

The signal is copying: a section of one product's `CLAUDE.md` pasted into another, or the same fix applied by hand to two copies of the same rule. One product needs no canon. The second product is when to start one.

## Steps

1. **List the repos** and clone them as siblings of the canon repo (`../<repo>`).
2. **Read each repo's foundational content**: `CLAUDE.md`, vision and values docs, design system, tone notes, glossary, workflow and release sections. One pass per repo, each with a self-contained prompt.
3. **List the conflicts.** For each topic, put the products' versions side by side. Expect most differences to be wording, not disagreement. Still list them: two wordings of one belief become two beliefs within a year. Number them C1, C2, ... in `03-conflicts/conflict-log.md`, each quoted with file and line.
4. **Look for phantom references**: a document cites a rule or file that doesn't exist. Either write it or remove the citation.
5. **Decide each conflict with the decision owner**, one at a time, with the real options laid out. Don't resolve by majority.
6. **Write the canon files** from the decisions. Where the oldest product is the source of most content, say so in the file; its copy is now protected from drift rather than replaced.
7. **Connect each product:** paste the `Canon Alignment` block into its `CLAUDE.md`, remove the restated sections (archive them if they hold history that has no home in canon), and write its `01-products/<product>.md` page. Edits in product repos stay uncommitted for their owners.
8. **Verify each product pass against its repo** (see `sync-checklist.md`) and log what review found.
9. **Write the roadmap's first Snapshot**, one row per product, each checked against its repo.

## What to expect

Most products will agree in substance and differ in words. A few findings will be real: a tagline that never reached the public site, a principles list copied with another product's examples still in it, two foundation documents in one repo that disagree. Those are the reason to do this.
