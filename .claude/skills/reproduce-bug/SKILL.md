---
name: reproduce-bug
description: Investigate and fix a bug by reproducing it first, then locking the fix in with a regression test. Use when given a bug report, error message, stack trace, failing test, unexpected behavior, or "X is broken".
---

# Reproduce Bug

**No reproduction, no fix.** A fix you can't demonstrate is a guess.

## Steps

1. **Capture the report.** Write down the expected behavior, the actual behavior, the steps,
   and the environment. Note what's missing and ask about it if it blocks you.

2. **Check `docs/FAILURE-LOG.md`** for past entries in this area.

3. **Reproduce it by observing.** Run the app or code path and trigger the bug yourself.
   Record the exact steps and the output (error, log lines, screenshot, wrong value).
   - Can't reproduce it? **Stop and report** what you tried and what you saw. Don't fix blind.

4. **Write a failing test** that captures the bug at the lowest level that still reproduces it.
   Run it and confirm it fails **for the right reason**: the same symptom, not a setup error.

5. **Find the root cause.** Trace from the symptom back to the cause using logs, traces,
   stepping through code and `git log` / `git blame` on the area. Explain the cause in one or
   two sentences. If you can't explain it, keep investigating.
   - Ask: is this one instance of a class of bugs? Where else could the same thing happen?

6. **Fix it minimally.** Change only what the root cause requires. No refactors, no drive-bys
   (see `docs/principles/06-atomic-changes.md`). Note related problems as separate follow-ups.

7. **Confirm the fix.**
   - The failing test now passes.
   - The original reproduction from step 3 now behaves correctly.
   - The full suite passes.
   - Then run the `verify-change` skill.

8. **Report** the reproduction steps, the root cause, the fix, the test added, the before and
   after evidence, and any follow-ups (other places the same bug class could occur).

9. **Capture the lesson if it's systemic.** If the bug came from a missing guardrail or an unclear
   convention, use the `capture-lesson` skill.

## Common failure modes

- Fixing the symptom where it appears instead of where it originates
- A "regression test" that passes even without the fix
- Adding defensive checks everywhere instead of finding the cause
- Widening scope into a refactor mid-fix
