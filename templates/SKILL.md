---
name: <kebab-case-name>
description: <What it does, in one sentence.> Use when <concrete triggers: phrases the user says, situations, file types>.
---

<!-- HOW TO USE THIS TEMPLATE
  1. Copy to .claude/skills/<kebab-case-name>/SKILL.md
  2. The `description` decides when the skill triggers. Be specific about WHEN, not just WHAT.
  3. Write steps as imperatives. Number them. Each step should be checkable.
  4. Before relying on it, write 3+ eval cases in evals/<kebab-case-name>/ (see evals/README.md).
  5. Delete this comment. -->

# <Skill Title>

<One or two sentences: the goal and the principle behind it.>

## When NOT to use

- <Situations that look similar but need a different skill or approach>

## Inputs needed

- <What must be known before starting. If it's missing, ask.>

## Steps

1. **<Verb phrase>.** <Detail. Point to exact files, commands or golden examples.>
2. **<Verb phrase>.** <Detail.>
3. **Verify.** <How to prove this skill's outcome is correct. Usually: run the `verify-change` skill.>
4. **Report.** <What the output or summary should contain.>

## Rules

- <Hard "never / always" rules for this procedure>

## Common failure modes

<!-- Grows over time. Each entry should trace back to docs/FAILURE-LOG.md. -->

- <Mistake agents make here> → <what to do instead>

## Examples

<!-- Optional. A short worked example of good output. -->
