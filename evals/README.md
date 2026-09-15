# Evals: Test Skills Like Software

A skill is a program whose runtime is a model. Treat it that way: **define the expected behavior,
test it across scenarios and models, score the output, and improve it iteratively.** Without
evals, every skill edit is a guess, and every model upgrade is a silent regression risk.

## When to write evals

- Before promoting a task category's trust level (see `docs/TRUST.md`)
- For any skill you rely on daily or that runs unsupervised (L3+)
- After a skill failure: add the failing scenario as a new case first, then fix the skill

## Layout

```
evals/
├── README.md
├── _case-template.md
├── RESULTS.md                    # Scorecard over time
└── <skill-name>/
    ├── fixtures/                 # Repo states, inputs, seed data the cases need
    └── cases/
        ├── 01-happy-path.md
        ├── 02-edge-<thing>.md
        ├── 03-should-not-trigger.md
        └── 04-regression-<failure-log-#>.md
```

## Writing a good suite

For each skill, cover these:

| Case type | Purpose |
|---|---|
| **Happy path** | The common, clean scenario |
| **Edge cases** | Ambiguous input, missing info, unusual repo state |
| **Negative / should-not-trigger** | Similar-looking requests where this skill is wrong |
| **Adversarial** | Tempting shortcuts, such as a failing test that "could just be deleted" |
| **Regression** | One per `FAILURE-LOG` entry this skill was changed to fix |

Start with 3–5 cases. Add one every time the skill fails in real use.

## Scoring: deterministic first, judgment second

1. **Deterministic checks** (most reliable): do the tests pass? Were only in-scope files touched?
   Was a test added? Were forbidden patterns avoided (ignore comments, deleted tests)?
   Does the output contain the required evidence section?
2. **Rubric scoring**: a human, or an LLM judge with a precise rubric, scores the
   qualitative criteria on 0–2 (0 = failed, 1 = partial, 2 = met).
3. **LLM-as-judge, carefully**: spot-check the judge against human scores before trusting it.

## Running evals

**Run each case several times.** Model output varies, so a single pass tells you little.

A simple manual or scripted loop:

1. Create a clean, isolated copy of the fixture repo state (a fresh git worktree or temp clone)
2. Run the agent headless with the case's prompt, e.g. `claude -p "<case prompt>"`
3. Apply the deterministic checks to the resulting repo state and output
4. Score the rubric
5. Record the results in `RESULTS.md`

Repeat across the models you use, and **re-run the whole suite after every skill change and every
model upgrade.**

## Iterating

- Pass rate dropped after a skill edit? Revert the edit or fix it. Treat it like a failing test.
- A case fails on every model? The skill is probably unclear. Fix the skill, not the case.
- A case fails on only one model? Decide whether that model is supported for this skill.
- Consistently 100%? Add harder cases. The suite has stopped teaching you anything.
