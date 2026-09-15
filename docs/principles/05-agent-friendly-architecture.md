# 05 — Design the Codebase for Agents

> **The easiest shortcut available to an agent should also be the correct architectural path.**

Agents pattern-match on what already exists. A codebase that's predictable, consistent and
bounded gets correct code by default. A codebase full of exceptions gets exceptions.

## Principles

1. **Predictable structure.** Every feature has the same shape. If you've seen one, you've seen them all.
2. **Colocate by feature, not by layer.** Keep a feature's UI, logic, data access, tests and types
   together. Don't scatter them across `components/`, `services/`, `utils/` and `tests/`.
3. **Clear boundaries.** Each module has one public entry point. Internals stay private.
   Allowed dependencies are written down *and enforced* (see [04](04-hard-constraints.md)).
4. **One way to do each thing.** One data-fetching pattern, one form pattern, one error pattern.
   Two ways means the agent picks at random.
5. **Golden examples.** Name one reference implementation per pattern in `ARCHITECTURE.md`.
   "Build it like `features/<example>`" is the most effective instruction you can give.
6. **Greppable names.** Use unique, descriptive, consistent names. Avoid generic files like
   `utils.ts`, `helpers.py` or `misc/`. An agent should find anything in two searches or fewer.
7. **Explicit over magic.** Hidden registration, reflection and convention-over-configuration
   that isn't written down all hurt agents. Explicit wiring is searchable.
8. **Small, focused files.** Agents read and edit whole files more reliably when files are short.
9. **Separate and mark generated code.** Put it in a clear location with a "DO NOT EDIT" header,
   and document the regeneration command.
10. **Docs live near code.** A short README in a complex module beats a wiki nobody updates.

## Example feature anatomy (adapt to your stack)

```
features/<feature-name>/
├── index.<ext>          # Public API: the only thing other modules import
├── <feature>.ui.<ext>   # Presentation
├── <feature>.logic.<ext># Pure logic, easy to unit test
├── <feature>.data.<ext> # Data access / API calls
├── <feature>.types.<ext>
├── <feature>.test.<ext> # Tests colocated with the code they test
└── README.md            # Optional: non-obvious decisions
```

## Agent-readiness checklist

- [ ] Can an agent find where X lives in two searches or fewer?
- [ ] Is there exactly one obvious place for a new feature to go?
- [ ] Does every common pattern have a named golden example?
- [ ] Are module boundaries enforced by tooling, not only documented?
- [ ] Can one feature be deleted without edits scattered across the codebase?
- [ ] Is generated code clearly separated and marked?

## Refactoring for agents is real work

Restructuring for predictability costs time and tokens up front. Do it incrementally:
every time an agent struggles in an area, make that area more conventional.
