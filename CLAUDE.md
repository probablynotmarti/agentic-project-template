# CLAUDE.md

<!-- Loaded into every agent session. Keep it short (under ~150 lines). Link to docs; don't inline them.
     Everything marked FILL-IN is per-project. Delete these comments once filled. -->

## Project

<!-- FILL-IN: One paragraph. What is this, who is it for, what stage is it in (prototype / beta / production)? -->

## Commands

<!-- FILL-IN: The agent verifies its work with these. If a row can't be filled, that's an infrastructure gap. Note it in docs/GUARDRAILS.md. -->

| Purpose | Command |
|---|---|
| Install deps | `FILL-IN` |
| Run app (dev) | `FILL-IN` |
| Typecheck | `FILL-IN` |
| Lint / format | `FILL-IN` |
| Unit tests (all) | `FILL-IN` |
| Single test file | `FILL-IN` |
| Integration / e2e | `FILL-IN` |
| **Full pre-PR check** | `FILL-IN` ← must pass before any PR |
| Logs / traces | `FILL-IN` (where to look at runtime behavior) |
| Seed / reset local data | `FILL-IN` |

## How to work here

1. **Understand before editing.** Read the relevant section of `docs/ARCHITECTURE.md` and the nearest existing example of what you're building. Copy its shape.
2. **Plan first for anything non-trivial.** State the files you'll touch and why. Check `docs/TRUST.md` to see whether you need approval before starting.
3. **One concern per change.** Don't mix refactors, formatting or drive-by fixes into a feature. See `docs/principles/06-atomic-changes.md`.
4. **Take the conventional path.** New features follow the `add-feature` skill. Don't invent new structures.
5. **Verify, don't claim.** "Done" means you ran it and have evidence. Use the `verify-change` skill.
6. **Bugs: reproduce first.** Use the `reproduce-bug` skill. No fix without a reproduction.
7. **If a guardrail blocks you, fix the code, not the guardrail.** Never disable lint rules, skip or delete tests, loosen types, or add ignore comments (`@ts-ignore`, `noqa`, `eslint-disable`, `--no-verify`) without asking.
8. **When the user corrects you on something likely to recur**, use the `capture-lesson` skill.
9. **Check `docs/FAILURE-LOG.md`** before working in an area. Known mistakes are listed there.

## Boundaries

<!-- FILL-IN: Adjust per project. Be concrete. Paths beat adjectives. -->

- **Never:** commit secrets or `.env` files · edit generated files (`FILL-IN: paths`) · modify already-applied migrations · push to `main` · `FILL-IN`
- **Ask first:** adding dependencies · schema or data-model changes · public API or contract changes · deleting files · changing CI, lint or test config · anything under `FILL-IN: sensitive paths`
- **Go ahead:** everything else inside the task's scope

## Map

| Need | Read |
|---|---|
| Where things live, what may import what | `docs/ARCHITECTURE.md` |
| Naming, patterns, "we do X not Y" | `docs/CONVENTIONS.md` |
| What's automatically enforced | `docs/GUARDRAILS.md` |
| What you may do unsupervised | `docs/TRUST.md` |
| Mistakes agents have made here before | `docs/FAILURE-LOG.md` |
| Why we work this way | `docs/principles/` |

## Project-specific notes

<!-- FILL-IN: Gotchas that don't fit anywhere else. Keep each to one line. Move each one into a guardrail or doc as soon as you can. -->
