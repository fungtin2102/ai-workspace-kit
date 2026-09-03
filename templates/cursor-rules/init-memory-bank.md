# Init Memory Bank

When `memory-bank/` is missing or incomplete, create the following structure.

## Core Files

- `projectbrief.md`: goals, scope, non-goals, and delivery constraints.
- `productContext.md`: users, scenarios, core workflows, and experience goals.
- `systemPatterns.md`: architecture, module relationships, data flow, design patterns, and lessons learned.
- `techContext.md`: stack, runtime environment, dependencies, commands, and deployment constraints.
- `activeContext.md`: current focus, recent changes, active decisions, and next steps.
- `progress.md`: completed work, todo items, risks, milestones, and decision history.

## Multi-Module Files

- `orchestrator-status.md`: orchestrator session summary.
- `module-<MODULE_NAME>-status.md`: per-module progress.
- `<TOPIC>.md`: complex topics, interface contracts, testing strategy, or deployment notes.

## Initialization Principles

- Mark unknown information as `TODO`; do not invent facts.
- Write project facts, not chat noise.
- Record why decisions were made, not only what changed.
- Let draft decisions stabilize in `dev-doc/` or `memory-bank/` before promoting them to formal docs.
