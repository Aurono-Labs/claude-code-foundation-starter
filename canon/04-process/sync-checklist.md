# Sync Checklist

What to do after a `00-canon/` file changes. `proposing-a-change.md` covers the decision; this covers the follow-through.

## When you edit a canon file

- [ ] Write the decision into the file itself. Don't leave the old text with a note that it changed.
- [ ] Log it in `03-conflicts/conflict-log.md` if it resolves a conflict or changes a decision. Wording polish doesn't need an entry.
- [ ] Check every `01-products/<product>.md` for a table, quote or example that cites the old version.
- [ ] If the change touches design tokens: every product that copied the tokens needs the same change in its own code.

## When you add a canon file

- [ ] Add it to `README.md`'s structure tree.
- [ ] Add it to the `Canon Alignment` block in `README.md` if products should check it at a specific moment.
- [ ] Each product's `CLAUDE.md` needs the new pointer, edited in that repo.

## When a canon pass runs on a product

1. **Give the pass a self-contained prompt.** It starts with no memory of other passes. Name the canon files to read first and the exact tasks; quote the stale lines rather than describing them.
2. **Let it propose before it writes** anything that's a judgment call (archive or delete, a rename target, a placement). Mechanical fixes (adding the pointer block, fixing a citation) don't need a check-in.
3. **Verify against the repo afterwards, not against the pass's own summary.** Grep for the specific claims.
4. **Fix what the review finds**, and log it in the product's drift log as "accidental, fixed on review": that says something about how thorough the pass was.
5. **Commit the canon side here.** Edits made in the product repo stay uncommitted for its owner.
6. **Say in the log entry what the pass wrote into the product repo, and check on the next pass that it's still there.**

## What doesn't sync by itself

- A product's `CLAUDE.md` can grow its own "principles" or "vision" section again after a pass. Only a periodic grep across the product repos for phrases from `01-values-and-vision.md` catches it.
- Copied design tokens don't follow canon automatically.
- Canon-authored edits in a product repo stay uncommitted, so they can vanish into a stash or a reset without anyone noticing.
- **A finding can go stale like a decision can.** "X is broken" or "Y is named wrong" can be repeated from page to page long after it stopped being true, or without ever having been true. Re-verify a finding before restating it, and correct it visibly where it was recorded.
