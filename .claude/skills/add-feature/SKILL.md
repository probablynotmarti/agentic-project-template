---
name: add-feature
description: 
---

# Add Feature

<!-- FILL-IN: Per-project skill. Replace every FILL-IN with this project's real paths and commands.
     Agents: if this file still contains FILL-IN markers, tell the user it isn't configured yet.
     Then follow the nearest golden example in docs/ARCHITECTURE.md and share a plan before editing. -->


## Steps

1. **Clarify acceptance criteria.** List what the user or caller can do when this is done.
   Ask if it's unclear. Check `docs/TRUST.md` for the "New features" level.

2. **Find the golden example.** Open the reference implementation for this kind of feature
   (listed in `docs/ARCHITECTURE.md` → Golden examples). Copy its structure exactly.
   - Reference for this project: `FILL-IN: path/to/golden/feature`

3. **Plan the slice.** List the files you'll create or change. If the change is bigger than one
   atomic PR, propose how to split it (prep refactor → feature, or vertical slices).

4. **Scaffold in the conventional location.**
   - Location: `FILL-IN: e.g., features/<feature-name>/`
   - Required files: `FILL-IN: e.g., index, ui, logic, data, types, test`
   - Scaffold command, if one exists: `FILL-IN or delete this line`

5. **Wire it up the standard way.**
   - Routing / registration: `FILL-IN`
   - Data access goes through: `FILL-IN: e.g., the feature's data module, never direct DB calls from UI`
   - State management: `FILL-IN`
   - Styling / components: `FILL-IN: e.g., design tokens from X, components from Y`

6. **Respect the boundaries.** Other modules import only from the feature's public entry point.
   Don't reach into another feature's internals (see `docs/ARCHITECTURE.md` → Boundaries).

7. **Write the tests.** At minimum:
   - `FILL-IN: e.g., unit tests for logic, one integration test for the happy path, one for the main error path`

8. **Verify.** Run the `verify-change` skill, including running the app and using the feature.

9. **Open the PR** using `.github/pull_request_template.md`.

## Project-specific gotchas


