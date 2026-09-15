# 04 — Hard Constraints Beat Prompts

Telling an agent "don't do X" works most of the time. Making X **impossible or loudly failing**
works every time. Prefer machines to memory.

## Enforcement hierarchy (strongest → weakest)

1. **Impossible by construction:** types, module boundaries, private APIs, the right abstraction
2. **Compiler / typechecker error**
3. **Lint rule error**, with a message that explains the fix
4. **Test failure**
5. **CI check**: required status, dependency restrictions, size and coverage gates
6. **Agent hook**: blocks a tool call or file edit before it happens
7. **Skill instruction**: a procedure the agent follows
8. **`CLAUDE.md` prompt**: a rule the agent is told
9. **Human review comment**: caught after the fact, by a tired person

**Push every rule as high up this list as you can.** Levels 7–9 are where rules *start*,
not where they should stay.

## The promotion rule

> **Write the same review comment twice → open a guardrail task.**

Keep a tally in `docs/GUARDRAILS.md`. Recurring comments are free requirements for your tooling.

## Write error messages for agents

Agents read error output and act on it. A good guardrail message says **what's wrong, why,
and what to do instead**:

```
✗ features/billing must not import from features/auth/internal.
  Use the public API: import { getSession } from "features/auth".
  See docs/ARCHITECTURE.md#boundaries
```

## Common guardrails by concern

| Concern | Enforce with (examples; pick what fits your stack) |
|---|---|
| Module boundaries | Import-restriction lint rules, dependency-graph checkers, package visibility |
| Banned APIs / patterns | Custom lint rules, restricted-syntax rules, grep checks in CI |
| Type safety | Strict compiler mode, no implicit any, CI fails on type errors |
| Dependencies | Allowlist or lockfile review, CI fails on new deps without approval |
| Formatting | Formatter run in a pre-commit hook or post-edit agent hook |
| Secrets | Secret scanner in pre-commit and CI |
| Test integrity | Coverage floor on changed lines, CI fails on `.only` / `skip` |
| Generated files | CI regenerates and diffs, and the file header says "DO NOT EDIT" |
| Sensitive paths | CODEOWNERS plus agent hooks that block edits |

## Protect the guardrails themselves

Agents take the easiest path. Sometimes that path is "loosen the rule".

- Lint, type, test and CI config are **ask-first** in `CLAUDE.md`
- Use CODEOWNERS on config files so changes need human review
- CI fails on new ignore comments (`@ts-ignore`, `eslint-disable`, `noqa`) unless they carry a justification
- Use agent hooks or permission deny rules to block edits to guardrail config

## When a prompt is still right

Use a prompt or skill when the rule needs **judgment** (for example, "prefer clarity over cleverness"),
or while you're still learning what the rule should be. Once it's clear and repeatable, automate it.
