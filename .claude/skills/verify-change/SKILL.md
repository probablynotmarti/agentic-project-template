---
name: verify-change
description: Prove a code change actually works before calling it done, and report evidence. Use after implementing any change, before opening a PR or saying "done", or when asked "does it work?" / "did you test it?".
---

# Verify Change

"Done" means **observed working, with evidence**. It doesn't mean "code written".
Principles: `docs/principles/03-verification.md`.

## Steps

1. **Restate what should now be true.** One or two sentences of expected behavior,
   including edge cases. If you can't say it, the task is underspecified. Ask.

2. **Check the scope.** Run `git diff --stat`. Every changed file should belong to this task.
   Revert or flag anything outside scope.

3. **Run the static checks** using the commands in `CLAUDE.md` → Commands: typecheck and lint.
   Fix any failures in the code. Never silence them with ignore comments or config changes.

4. **Test the change itself.**
   - Is there a test that exercises the changed code? If not, write one.
   - **Prove the test is meaningful:** it should fail without your change. Temporarily revert
     the change or reason about it explicitly, and say which you did.
   - Run the single test file, then the full suite.

5. **Observe real behavior.** Run the app (`Run app` command) and exercise the change the way a
   user or caller would: click through the UI, call the endpoint, run the CLI. Check logs and
   traces for errors or warnings you introduced.
   - For UI: take a screenshot or describe exactly what was rendered.
   - For bugs: repeat the original reproduction and confirm it now behaves correctly.

6. **Run the full pre-PR check** command from `CLAUDE.md`. It must pass.

7. **Report evidence** in this format:

   ```
   Verification
   - Ran: <command> → <result>
   - Observed: <action taken in running app> → <what happened>
   - Bug repro (if fix): before → <broken>, after → <fixed>
   - Not verified: <what you couldn't check, and why>
   ```

## Rules

- **Never** change a test's assertions just so it passes. If a test is wrong, say so and explain why.
- **Never** mock the thing you're testing.
- **Always** fill in "Not verified". Write "nothing" only if that's true.
- If you can't run or observe something (missing command, no environment, no data), stop and
  report it as an infrastructure gap for `docs/GUARDRAILS.md`. Don't paper over it.

## Common failure modes

- Reporting "tests pass" when no test touches the changed lines
- Running only new tests, not the full suite
- Declaring UI work done without rendering it
- Treating "no errors" as proof of correct behavior
