# Guardrails

<!-- FILL-IN: Per-project. The inventory of rules the machine enforces, plus the pipeline of rules that should be.
     Principles: docs/principles/04-hard-constraints.md -->

## Enforced rules

Rules that fail loudly without anyone remembering them.

| Rule | Enforced by | Level | Added | Origin |
|---|---|---|---|---|
| Types must check | `FILL-IN` | compiler / CI | | baseline |
| Lint must pass | `FILL-IN` | lint / CI | | baseline |
| Tests must pass | `FILL-IN` | CI | | baseline |
| No secrets committed | `FILL-IN` | pre-commit / CI | | baseline |
| FILL-IN | | | | FAILURE-LOG #__ |

## Review-comment tally

Every time you leave the same review comment, add a tick. **Two ticks → create a guardrail task.**

| Review comment (paraphrased) | Count | Status |
|---|---|---|
| FILL-IN | ✓ | watching / guardrail task open / automated |

## Guardrail backlog

Candidates, ordered by how often they bite.

- [ ] FILL-IN: rule, proposed enforcement tool, source (tally row or failure-log entry)

## Infrastructure gaps

Things agents can't verify yet (see docs/principles/03-verification.md).

- [ ] FILL-IN: e.g., "no way to run e2e tests locally", "no seed data for X"

## Protected config

Changes to these require human approval (CODEOWNERS / agent hooks):

- `FILL-IN` (lint config, tsconfig / compiler config, CI workflows, test config, this file)
