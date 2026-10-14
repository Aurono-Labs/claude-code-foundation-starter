# Release Workflow

> Pre-filled: this is the method, not an interview answer. It applies to products with a staged deployment (a test environment or device before production). A product without one can skip it until it has one.

Each such product's `CLAUDE.md` reproduces the three stages with its own hostnames, repo names and file paths, and says at the top: *"Releases follow `<org>-canon/00-canon/09-release-workflow.md`."*

This is a different axis from `08-development-workflow.md`. That file covers how one change gets built and closed; this one covers how a batch of closed changes reaches users. One release usually bundles several Phase 6 closings.

## Stage 1: Dev machine

- All test suites green; a manual walk through any visible behavior.
- The change is merged to the main branch.
- An entry is added to the product's pending release notes file.
- **Gate:** nothing reaches Stage 2 with failing tests or an unexplored regression.

## Stage 2: Pre-release on the acceptance environment

- **Audit the pending release notes against the previous tag before drafting the version bump.** Compare with the previous tag's notes (`git tag -l --format='%(contents)' v<prev>`) and drop anything that already shipped. Walk `git log v<prev>..HEAD --oneline` and add a note for every user-visible change that's missing one. The pending file clears only after a successful Stage 3, so after a skipped or rolled-back release it carries stale content.
- **After a failed soak, `v<prev>` is still the last tag that reached Stage 3, never the abandoned pre-release.** Re-run the full audit against it for the retry tag. The range now spans the original batch and the fix, and the notes must cover both. This is the rule most likely to break quietly.
- **A fix for something the soak found gets its own release note,** however small.
- Bump the version through a small pull request; merge it.
- Tag with the release notes as the annotation (`git tag -a vX.Y.Z --cleanup=verbatim -F <notes-file>`); `--cleanup=verbatim` keeps `#` headings that git would otherwise strip. Push the tag.
- Publish as a **pre-release**, explicitly not "latest", so existing installs keep being offered the previous release.
- Deploy to the acceptance environment. **Claude gives the commands; a human runs them.**
- Soak for as long as the change warrants: at least through the next scheduled run and any time-bound tests; longer for anything that touches durable state (databases, ledgers, logs).
- Close the matching functional test entries with a note that they passed on acceptance.
- **Gate:** a regression means: fix it, add its release note, bump to the next pre-release version, and repeat Stage 2 from the top. **Tags are immutable; never re-tag a failed attempt.**

## Stage 3: Promote to production

- Mark the release as latest. This is the switch that makes existing installs offer the update; flip it on purpose, after Stage 2 soaked clean.
- Deploy to production: the same artifact as acceptance.
- Re-run the small set of startup and health checks on production.
- Clear the pending release notes file, or move its entries into a changelog.
- Mark the plan item done with the production date.

## Claude's role

- **Stage 1:** code, tests, pull requests, through the development workflow.
- **Stage 2:** draft the version bump and the tag message. The human pushes the tag, publishes the pre-release and deploys.
- **Stage 3:** draft the closing commits. The human promotes the release and deploys.

**Never deploy to a real environment or device automatically.** If the operator says "ship it" during Stage 1, ask which stage they mean: "ship" can mean merge, or promote to latest.
