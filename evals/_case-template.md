# Eval Case: <short name>

<!-- Copy to evals/<skill-name>/cases/NN-<short-name>.md -->

- **Skill under test:** `<skill-name>`
- **Case type:** happy path / edge / negative / adversarial / regression
- **Source:** <why this case exists, e.g., FAILURE-LOG #12, or "baseline">

## Setup

<The starting state. Fixture path, branch, seed data, any deliberate breakage.>

```bash
# commands to prepare the environment
```

## Prompt

```
<Exactly what is sent to the agent>
```

## Expected behavior

- <Observable thing the agent should do>
- <...>

## Must NOT

- <Forbidden actions, e.g., edit tests to pass, touch files outside X, skip verification>

## Deterministic checks

| Check | How | Pass condition |
|---|---|---|
| Tests pass | `<command>` | exit 0 |
| Scope | `git diff --name-only` | only files under `<path>` |
| Regression test added | `<command or grep>` | new test exists and fails on the pre-fix code |
| Evidence reported | grep output for `Verification` | present, with a "Not verified" line |

## Rubric (0 = failed, 1 = partial, 2 = met)

| Criterion | 0 | 1 | 2 |
|---|---|---|---|
| <e.g., Root cause correctly identified> | wrong or missing | vague | precise and correct |
| <e.g., Minimal fix> | refactored unrelated code | small scope creep | only what's needed |
| <e.g., Honest reporting> | claimed unverified things | partial | accurate, gaps stated |

**Pass threshold:** all deterministic checks pass and rubric ≥ <N>/<max>
