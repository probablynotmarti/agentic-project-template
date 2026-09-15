# Agentic Project Template

A starting structure for projects where AI agents write a meaningful share of the code.
It's based on notes from Lauren Tan's workshop on agentic engineering.

> **Core idea:** reliable agentic coding comes mostly from the system around the agent:
> verification, architecture, tests, CI and feedback loops. A smarter model or one
> perfect prompt matters much less. Copy the infrastructure, not the PR counts.

---

## Two kinds of files

| Kind | Marker | Rule |
|---|---|---|
| **General** | none | Same for every project. Improve them *here in the template*, not per project. |
| **Per-project** | `<!-- FILL-IN -->` | Adjust for each use case. Start small and fill them in as you learn. |

## File map

```
.
├── CLAUDE.md                          [per-project]  Agent entry point, loaded every session
├── .claude/skills/
│   ├── verify-change/SKILL.md         [general]      Prove a change works with evidence
│   ├── reproduce-bug/SKILL.md         [general]      Reproduce → failing test → fix → confirm
│   ├── capture-lesson/SKILL.md        [general]      Turn a mistake into a guardrail or skill
│   └── add-feature/SKILL.md           [per-project]  The conventional path for new features
├── docs/
│   ├── principles/                    [general]      The "why". Read once, reference often
│   │   ├── 01-philosophy.md
│   │   ├── 02-trust-ladder.md
│   │   ├── 03-verification.md
│   │   ├── 04-hard-constraints.md
│   │   ├── 05-agent-friendly-architecture.md
│   │   ├── 06-atomic-changes.md
│   │   └── 07-cost-and-payoff.md
│   ├── ARCHITECTURE.md                [per-project]  Map, boundaries, golden examples
│   ├── CONVENTIONS.md                 [per-project]  "We do X, not Y"
│   ├── GUARDRAILS.md                  [per-project]  Enforced rules and review-comment tally
│   ├── TRUST.md                       [per-project]  What agents may do unsupervised
│   └── FAILURE-LOG.md                 [per-project]  Recurring agent mistakes and their fixes
├── evals/
│   ├── README.md                      [general]      How to test skills like software
│   ├── _case-template.md              [general]      Copy this for each eval case
│   └── RESULTS.md                     [per-project]  Scorecard over time
├── templates/
│   └── SKILL.md                       [general]      Copy this to write a new skill
└── .github/pull_request_template.md   [general]      Atomic scope and verification evidence
```

## Starting a new project

1. **Copy the template into the project.** This won't overwrite existing files:
   ```bash
   rsync -a --ignore-existing --exclude README.md ~/Desktop/agentic-project-template/ /path/to/project/
   ```
2. **Fill in `CLAUDE.md` → Commands first.** An agent can't verify its work without them.
3. **Set `docs/TRUST.md` to L1** (supervised, local) for every task category.
4. **Fill in `ARCHITECTURE.md` and `CONVENTIONS.md` lazily.** Add a section when an agent gets something wrong because it wasn't written down.
5. **List the placeholders that are left:**
   ```bash
   grep -rn "FILL-IN" --exclude=README.md .
   ```
6. **Using other agent tools too?** `ln -s CLAUDE.md AGENTS.md`

## Pick your adoption tier

You don't need all of this on day one. See [07-cost-and-payoff](docs/principles/07-cost-and-payoff.md).

| Tier | Use for | Keep |
|---|---|---|
| **Minimal** | Prototypes, weekend hacks | `CLAUDE.md` + `verify-change` skill |
| **Standard** | Real projects, solo or small team | Everything except `evals/` |
| **Full** | Team projects, parallel/cloud agents, auto-merge | Everything |

## The operating loop

```
 task ─▶ plan ─▶ implement ─▶ VERIFY ─▶ review ─▶ merge
                                 │         │
                                 ▼         ▼
                         mistake? ─▶ capture-lesson ─▶ guardrail / skill / doc
                                                            │
                                                            ▼
                                                  eval it ─▶ promote trust
```

Every recurring mistake should leave the system a little stronger. That's how this
template is meant to be used.
