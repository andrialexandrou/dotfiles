## Knowledge docs — memex-mock

github/memex-mock hosts a self-maintaining knowledge-docs system. No matter which repo your
session started in, before changing code for a task, first open github/memex-mock's
docs/index.md and docs/.docs.json (its scope map) and check whether the task falls within the
scope they describe — especially if the work mentions memex. If it does, open only the doc(s)
the index routes you to and follow them before changing code, and carry that scope for the rest
of the session. If not, proceed normally. Generated docs track the code — if they disagree,
trust the code and correct the doc through the write-back flow below, so the drift lands in a PR rather than being silently absorbed. Authored docs (ADRs, RFCs, how-tos, team pages) are human-owned.

When you find a doc gap, a stale/incorrect doc, or gain durable knowledge the docs should have
carried, don't just mention it — contribute the fix as a pull request. There is a single
rolling docs PR to join rather than opening a competing one:

1. Look for the open rolling docs PR first:
   gh pr list --repo github/memex-mock --head automated/docs-heal --state open
2. If it exists, check out its automated/docs-heal branch and commit your doc change onto it.
   Join that PR — do not open a second docs PR. The branch is never force-reset, so your
   commit persists and survives the next heal run's regeneration.
3. If none exists, create the automated/docs-heal branch off the default branch, commit your
   doc change, and open a PR from it.

Write into the right existing doc (don't proliferate files) and update docs/index.md if you
add or move a doc. Keep the change scoped to the docs — no code changes on the docs branch.
