---
name: capture-lesson
description: Turn a correction or recurring agent mistake into a durable systemic fix (guardrail, test, skill update, or doc) and log it. Use when the user corrects the agent's approach, a review comment repeats, the same failure happens twice, or the user says "remember this" / "don't do that again".
---

# Capture Lesson

Every recurring mistake should leave the system stronger. Saying "I'll remember next time"
doesn't count. The next session won't remember.

## Steps

1. **State the mistake neutrally.** Say what happened and what should have happened. One sentence each.

2. **Find the systemic root cause.** Ask what, in the environment, allowed this:
   - Was the rule written down anywhere? (If not, it's a doc gap.)
   - Was it written down but easy to miss or ambiguous? (That's a skill or doc clarity gap.)
   - Was the wrong path easier than the right one? (That's an architecture gap.)
   - Could a machine have caught it? (That's a guardrail gap.)

3. **Pick the strongest feasible fix** (see `docs/principles/04-hard-constraints.md`):

   | Fix type | Use when | Where |
   |---|---|---|
   | **Guardrail** | The rule is clear and mechanically checkable | Lint rule, type, CI check, hook → log in `docs/GUARDRAILS.md` |
   | **Test** | It's a behavior that must not regress | Test file next to the code |
   | **Architecture** | The wrong path was the easy path | Refactor task → note in `docs/ARCHITECTURE.md` |
   | **Skill update** | A procedure was followed wrong or missing | `.claude/skills/<name>/SKILL.md` → then re-run its evals |
   | **Doc** | It's a convention needing judgment | `docs/CONVENTIONS.md` "We do X, not Y" table |
   | **CLAUDE.md** | Last resort: short, universal, always relevant | `CLAUDE.md` |

4. **Log it in `docs/FAILURE-LOG.md`.** Fill in date, area, what happened, root cause, fix type,
   fix link and status.
   - **If a similar entry already exists, the previous fix was too weak.** Escalate it one step up the table.

5. **If the lesson came from a review comment,** add a tick in the tally in `docs/GUARDRAILS.md`.
   On the second tick, add it to the guardrail backlog.

6. **Propose, don't silently apply.** Show the user the proposed fix. Changes to guardrail
   config, CI or skills need approval (see `CLAUDE.md` → Boundaries).

7. **Keep the fix atomic.** A guardrail or skill change is its own PR, separate from the task
   that exposed it.

## Common failure modes

- Only adding a line to `CLAUDE.md` when a lint rule was possible
- Logging a lesson that's too specific to prevent the next variant
- Making a skill longer instead of clearer
