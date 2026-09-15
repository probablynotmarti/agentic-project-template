# Conventions

<!-- FILL-IN: Per-project. Write only what isn't already enforced by a formatter or linter.
     When a row here becomes automated, move it to docs/GUARDRAILS.md and delete it from here. -->

## We do X, not Y

The highest-value section. Every row prevents a recurring mistake.

| Do | Don't | Why |
|---|---|---|
| FILL-IN | FILL-IN | FILL-IN |

## Naming

| Thing | Convention | Example |
|---|---|---|
| Files | FILL-IN | |
| Components / classes | FILL-IN | |
| Functions | FILL-IN | |
| Tests | FILL-IN | |
| Branches | `<type>/<short-description>` | `fix/login-redirect-loop` |

## Error handling

<!-- FILL-IN: How errors are raised, caught, surfaced to users, and logged. Link a golden example. -->

## Logging & observability

<!-- FILL-IN: Logger to use, levels, what must never be logged (PII, tokens), where logs go. -->

## Testing

<!-- FILL-IN -->
- Tests live: FILL-IN (e.g., colocated next to source)
- Each bug fix includes a regression test that fails before the fix
- Mock at: FILL-IN (e.g., the network boundary only, never internal modules)
- Test data comes from: FILL-IN

## UI / styling

<!-- FILL-IN: Design tokens source, component library, accessibility minimums. Delete if not applicable. -->

## Data & migrations

<!-- FILL-IN: How schema changes are made and reviewed. Delete if not applicable. -->
