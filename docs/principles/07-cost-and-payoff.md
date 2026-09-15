# 07 — Costs, Payoff and Sequencing

Agent-driven development has **real upfront costs**: refactoring, writing evals, building
guardrails, maintaining skills. Those cost time and tokens. The payoff comes when the system
compounds: every fix prevents a whole class of future mistakes, and the whole team moves faster.
That includes PMs and designers making safe contributions.

## Upfront costs

- Refactoring toward predictable, bounded architecture
- A fast, deterministic test suite and one-command verification
- Writing and maintaining skills
- Building and running evals (tokens × cases × runs × models)
- Custom lint rules, CI checks and hooks
- Your attention while watching agents closely at L1–L2

## Where the payoff comes from

- Recurring mistakes stop recurring, because they're enforced rather than remembered
- Review gets faster, because evidence arrives with the PR
- Agents can safely run in parallel and in the cloud
- Non-engineers can contribute because guardrails catch unsafe changes
- New humans onboard faster, because the docs agents need are the docs people need

## Recommended sequencing

Invest in this order. Each step makes the next one worth doing.

1. **Commands in `CLAUDE.md`**, so the agent can run and check things
2. **Verification:** one-command pre-PR check, plus the `verify-change` skill
3. **Failure log:** start writing down what goes wrong
4. **Guardrails:** automate the top recurring failures
5. **Architecture:** make the conventional path obvious, and name golden examples
6. **Skills** for recurring procedures
7. **Evals** for the skills you depend on most
8. **Scale:** parallel agents → cloud → triggers → narrow auto-merge

## Adoption tiers: match the investment to the project

| Tier | When | Use |
|---|---|---|
| **Minimal** | Prototype, throwaway, solo weekend | `CLAUDE.md` (commands + boundaries), `verify-change` |
| **Standard** | Real product, solo or small team | + principles, ARCHITECTURE, CONVENTIONS, GUARDRAILS, FAILURE-LOG, TRUST, all skills, PR template |
| **Full** | Team, parallel or cloud agents, auto-merge goals | + evals, CI enforcement of everything, trust metrics |

**Don't over-invest early.** A prototype with a full eval suite is procrastination.
A production system with no verification is a liability.

## Is it paying off? Track:

- Corrections per task (should trend down)
- First-pass PR acceptance (should trend up)
- Review time per PR (should trend down)
- Escaped bugs from agent PRs (should stay flat or low while volume grows)
- The same failure appearing twice in `FAILURE-LOG.md` (should approach zero)
