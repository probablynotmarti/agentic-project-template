# 02 — The Trust Ladder: Start Local, Then Scale

**Trust is the bottleneck to scaling.** You can't responsibly jump from one supervised agent
to dozens of autonomous ones. Agents earn trust gradually, through verification you can repeat.

## Levels

| Level | Mode | You do | Agent does |
|---|---|---|---|
| **L0** | Chat / autocomplete | Write the code | Suggest |
| **L1** | One agent, local, supervised | Watch each step, approve edits | Plan and implement in front of you |
| **L2** | One agent, local, auto-accept edits | Review the diff and verification evidence at the end | Implement and verify end to end |
| **L3** | 2–3 parallel agents, isolated worktrees | Assign tasks, review each PR | Work independently, one task per branch |
| **L4** | Cloud agents, triggered (bug reports, issues, schedules) | Review PRs as they arrive | Pick up work, reproduce, fix, open a PR |
| **L5** | Auto-merge for narrow categories | Audit samples, watch metrics | Ship through CI gates without human review |

## Rules

1. **Trust is per task category, not global.** An agent can be L4 for "fix a failing lint rule"
   and L1 for "change the auth flow". Track this in `docs/TRUST.md`.
2. **Blast radius caps the level.** Auth, payments, data deletion, migrations and security
   config stay at L1–L2 no matter how good the track record looks.
3. **Promotion needs evidence, not vibes.** For example: *10 consecutive tasks in this category
   merged without substantive correction, zero escaped bugs, evals passing.*
4. **Demote on incident.** An escaped bug or a bad merge drops that category one level until
   there's a fix in the system (a guardrail, skill or eval) and the category has earned trust again.
5. **Watch closely before you scale.** Do 1–2 agents locally until you can predict their
   failure modes. If you can't predict the failures, you're not ready for the next level.

## Prerequisites per level

| To reach | You need |
|---|---|
| L2 | One-command verification (`Full pre-PR check` in CLAUDE.md), a `verify-change` skill |
| L3 | Worktree or branch isolation, atomic task scoping, a PR template with evidence |
| L4 | Isolated cloud environment, reproducible setup, the `reproduce-bug` skill, trigger wiring |
| L5 | Evals for the category, strong CI gates, easy revert, monitoring and alerting |

## Metrics worth tracking

- **First-pass acceptance rate:** PRs merged without a change request
- **Correction count per task:** how often you had to redirect
- **Revert rate / escaped bugs:** the real signal of trust
- **Time to verify:** if review takes as long as writing it yourself, the system needs work
