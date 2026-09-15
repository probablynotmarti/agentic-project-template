# 03 — Verification: Close the Loop

An agent that only writes code is guessing. An agent that **runs the code and observes what
happens** is engineering. Give agents what they need to prove their own work.

## The verification ladder (weakest → strongest)

1. It compiles or parses
2. Types check
3. Lint passes
4. Existing tests pass
5. **New tests cover the change**, and they fail without it
6. Integration / e2e tests pass
7. **The app was run and the behavior was observed**: UI clicked through, API called, CLI invoked
8. **For bugs: the original reproduction now behaves correctly**
9. Logs and traces show the expected path, with no new errors or warnings

Aim as high as the change needs. A copy tweak needs rung 7. A data-layer change needs 5–9.

## What agents need access to

If an agent can't observe something, it can't verify it. **Every missing item is an
infrastructure to-do, not something the prompt can fix.**

- [ ] A one-command local dev environment
- [ ] A fast, deterministic test suite, plus the ability to run a single test
- [ ] Seed or fixture data, and a reset command
- [ ] Readable logs (structured, with a known location)
- [ ] Traces or request inspection for backend work
- [ ] A browser, simulator or emulator the agent can drive for UI work
- [ ] Screenshots or visual diffs for UI changes

## Evidence format

"Done" means evidence. Every PR includes:

```
Verification
- Ran: <exact command>  →  <result: pass / N tests / output excerpt>
- Observed: <what you did in the running app and what happened>
- Bug repro (if fix): before → <broken behavior>, after → <correct behavior>
- Not verified: <what you couldn't check, and why>
```

The **"Not verified"** line is required. Honest gaps beat implied coverage.

## Verification anti-patterns

- Saying "tests pass" when no test exercises the changed code
- Editing a test's assertions so it passes instead of fixing the code
- Mocking the very thing under test
- Claiming a fix without ever reproducing the bug
- Running only the tests the agent wrote and skipping the full suite
- Treating "no errors in the console" as proof of correct behavior

## Invest here first

Of everything in this template, verification infrastructure pays back first and most.
A fast, trustworthy `Full pre-PR check` command is worth more than any amount of prompting.
