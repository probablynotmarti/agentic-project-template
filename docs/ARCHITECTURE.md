# Architecture

<!-- FILL-IN: Per-project. Start with the Overview, the Directory map and one golden example.
     Add sections only when an agent gets something wrong because it wasn't written down.
     Principles behind this file: docs/principles/05-agent-friendly-architecture.md -->

## Overview

<!-- FILL-IN: 3–5 sentences. What the system does, the main moving parts, how a request/action flows through it. -->

## Stack

| Layer | Choice | Notes |
|---|---|---|
| Language | FILL-IN | |
| Framework | FILL-IN | |
| Data / storage | FILL-IN | |
| Auth | FILL-IN | |
| Hosting / infra | FILL-IN | |
| Testing | FILL-IN | |

## Directory map

<!-- FILL-IN: Top two levels only. One line per folder saying what belongs there. -->

```
FILL-IN/
├── ...
```

## Feature anatomy

<!-- FILL-IN: The standard shape every feature follows. Paste a real folder tree. -->

## Golden examples

<!-- FILL-IN: The single best reference implementation per pattern. Agents copy these. Keep them exemplary. -->

| Pattern | Reference | Notes |
|---|---|---|
| New feature / screen | `FILL-IN` | |
| Data fetching / API call | `FILL-IN` | |
| Form + validation | `FILL-IN` | |
| Background job / async | `FILL-IN` | |
| Test for the above | `FILL-IN` | |

## Boundaries

<!-- FILL-IN: What may depend on what. Mark each row as enforced (with the tool) or documented only.
     "Documented only" rows are candidates for docs/GUARDRAILS.md. -->

| Module | May import from | Must NOT import from | Enforced by |
|---|---|---|---|
| FILL-IN | | | `FILL-IN` / documented only |

## Where does X go?

| I'm adding… | It goes in… |
|---|---|
| FILL-IN | FILL-IN |

## External services

| Service | Used for | Local substitute (mock / emulator / sandbox) |
|---|---|---|
| FILL-IN | | |

## Key decisions

<!-- FILL-IN: Short ADR-style entries: Decision, Why, Date. Prevents agents from "fixing" deliberate choices. -->

- **YYYY-MM-DD** FILL-IN: decision (why)
