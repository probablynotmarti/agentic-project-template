# Agent Trust Levels

<!-- FILL-IN: Per-project. Start every category at L1. Promote only with evidence.
     Level definitions: docs/principles/02-trust-ladder.md -->

**Agents: find the category for your task below and follow its level.**
If your task isn't listed, treat it as **L1**: plan first and wait for approval.

| Level | Meaning for the agent |
|---|---|
| L1 | Share a plan and wait for approval. Pause at each significant step. |
| L2 | Implement and verify end to end, then present the diff and evidence for review. |
| L3 | Work in your own branch or worktree in parallel with other agents. Open a PR. |
| L4 | You may be triggered automatically. Open a PR; humans review it. |
| L5 | May auto-merge if all CI gates pass. |

## Current levels

| Task category | Level | Since | Evidence for current level | Promotion criteria for next level |
|---|---|---|---|---|
| Docs / comments / copy | L1 | FILL-IN | — | e.g., 10 merged without substantive edits |
| Tests (adding coverage) | L1 | | — | |
| Lint / type fixes | L1 | | — | |
| Bug fixes (isolated) | L1 | | — | |
| New features | L1 | | — | |
| Refactors | L1 | | — | |
| Dependency updates | L1 | | — | |
| FILL-IN | L1 | | — | |

## Capped categories (never above L2)

<!-- FILL-IN: High-blast-radius areas. -->

- Auth / permissions
- Payments / billing
- Data deletion, migrations, schema changes
- Security, CI and guardrail configuration
- FILL-IN

## History

| Date | Category | Change | Reason |
|---|---|---|---|
| FILL-IN | | L1 → L2 / L3 → L2 (demotion) | |
