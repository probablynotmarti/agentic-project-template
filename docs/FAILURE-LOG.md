# Failure Log

<!-- Per-project. Every agent mistake worth correcting goes here. Nothing gets closed without a systemic fix.
     The capture-lesson skill writes to this file. -->

**Agents: before working in an area, scan this log for entries in that area.**

## How to use

1. Something goes wrong (a bad output, a correction, a review comment, an escaped bug), so add an entry.
2. Find the **root cause in the system**, not just "the agent made a mistake". Ask: what was
   missing, ambiguous or unenforced?
3. Pick the **strongest fix** available (see `docs/principles/04-hard-constraints.md`):
   `guardrail` > `test` > `architecture` > `skill` > `doc` > `CLAUDE.md`
4. Link the fix. An entry stays **open** until one exists.
5. **Same failure twice means the last fix was too weak.** Move it up the hierarchy.

## Log

| # | Date | Area | What happened | Root cause | Fix type | Fix link | Status |
|---|---|---|---|---|---|---|---|
| 1 | YYYY-MM-DD | FILL-IN | FILL-IN | FILL-IN | guardrail / test / arch / skill / doc | FILL-IN | open / fixed |

## Patterns noticed

<!-- Themes across entries, e.g., "agents repeatedly bypass the data layer in feature X". These usually point to architecture work. -->
