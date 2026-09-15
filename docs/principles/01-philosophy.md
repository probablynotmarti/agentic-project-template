# 01 — Philosophy: Amplify Thinking, Don't Replace It

## The stance

Agents are **pair programmers**. They make coding faster. They don't take away the need to
understand, review and direct the work. The engineer stays accountable for every line that ships.

**The merge rule:** if you can't explain a change, you haven't reviewed it. Merging it
anyway is gambling.

## The head-chef model

You may write less code yourself. Your job moves up a level:

| Chef does | Engineer equivalent |
|---|---|
| Designs the kitchen | Designs the codebase so the easy path is the correct path |
| Mise en place | Prepares context: `CLAUDE.md`, skills, architecture docs, commands |
| Assigns stations | Splits work into atomic, well-scoped tasks |
| Tastes everything | Sets and enforces quality bars: verification, review, CI |
| Fixes the recipe, not just the plate | Turns every recurring mistake into a skill or guardrail |

## Where your time goes now

| Before | After |
|---|---|
| Typing implementation | Specifying intent and acceptance criteria |
| Debugging your own code | Reviewing verification evidence |
| Remembering conventions | Encoding conventions into tools |
| Fixing the same bug class again | Building the guardrail that prevents that class |

## Anti-patterns

- **Prompt golf:** hunting for the perfect prompt when the real fix is a test, a type or a lint rule.
- **Model shopping:** swapping models to fix what is really a system problem (missing verification, unclear architecture).
- **Rubber-stamp review:** approving because "the agent ran the tests" without checking the tests cover the change.
- **Scaling before trust:** jumping from one supervised agent to many autonomous ones. See [02-trust-ladder](02-trust-ladder.md).
- **Outsourcing understanding:** accepting code in an area you no longer understand. Your ability to direct the work decays.

## Bottom line

The durable lesson is the infrastructure behind high agent throughput: verification,
architecture, tests, CI and feedback loops. Headline numbers such as PRs per day are
self-reported and depend on context. Copy the system, not the stat.
