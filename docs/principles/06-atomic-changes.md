# 06 — Keep Changes Atomic

Small, focused changes are easier to **understand, review, revert and diagnose**.
That matters more when many changes come from agents.

## Rules

1. **One concern per PR.** A feature, a fix or a refactor. Never a mix.
2. **Separate refactors from behavior changes.** First a refactor PR with no behavior change,
   then a feature PR on top.
3. **Isolate mechanical changes.** Renames, moves, formatting and dependency bumps each get their own PR.
4. **Isolate schema and migration changes** from the code that uses them when you can.
5. **Every PR leaves `main` green** and deployable.
6. **No drive-by fixes.** If the agent spots something unrelated, it notes it and opens a
   separate task. It doesn't fold the fix in.

## Soft size guide (not a hard limit)

| Diff size (excluding generated / lockfiles) | Guidance |
|---|---|
| < ~200 lines | Ideal |
| ~200–400 | Fine if it's one clear concern |
| > ~400 | Probably splittable. Justify it in the PR description |

## Splitting strategies

- **Prep then change:** land the enabling refactor first, then the small feature change
- **Feature flags:** merge incomplete work dark, then enable it in a separate PR
- **Stacked PRs:** a chain of small dependent PRs, each reviewable on its own
- **Vertical slices:** thin end-to-end slices beat horizontal layers ("all the DB code first")

## For agents specifically

- **One task = one branch (or worktree) = one PR.**
- Write the task's scope into the plan and flag any file touched outside it.
- A bisect should land on a change small enough to understand at a glance.

## Commit messages

```
<type>(<area>): <imperative summary, ≤ 72 chars>

<why this change, not what; the diff shows what>
```

Types: `feat` · `fix` · `refactor` · `test` · `docs` · `chore` · `perf`
