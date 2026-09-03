# Codex Orchestrator Instructions - <ROOT_PROJECT>

This workspace is the orchestrator session for a multi-module project. It is responsible for global orchestration, task splitting, status summaries, and cross-module contracts. It should not primarily edit implementation code.

Read and follow first:
- `.cursor/rules/`
- `.clinerules/`
- `.ai-rules/roles/`
- `memory-bank/`
- `dev-doc/`

## Project Overview

- Root project: `<ROOT_PROJECT>`
- Description: `<ROOT_PROJECT_DESCRIPTION>`
- Root branch: `<ROOT_BRANCH>`
- Default module branch: `<DEFAULT_MODULE_BRANCH>`

## Excluded Paths

Fill this section for the target project. Examples:
- `archive/`: archived history; do not index, search, read, cite, or use as implementation reference.
- `legacy/`: deprecated implementation; do not inspect unless explicitly requested.
- Generated or heavy directories: `dist/`, `build/`, `target/`, `.venv/`, `node_modules/`.

## Always-On Module Sessions

| Module | Path | Responsibility | Git URL | Branch |
|--------|------|----------------|---------|--------|
| `<MODULE_A>` | `<MODULE_A_PATH>` | `<MODULE_A_DESCRIPTION>` | `<MODULE_A_GIT_URL>` | `<MODULE_A_BRANCH>` |
| `<MODULE_B>` | `<MODULE_B_PATH>` | `<MODULE_B_DESCRIPTION>` | `<MODULE_B_GIT_URL>` | `<MODULE_B_BRANCH>` |

## On-Demand Module Sessions

| Module | Path | Responsibility | Git URL | Branch |
|--------|------|----------------|---------|--------|
| `<MODULE_DOCS>` | `<MODULE_DOCS_PATH>` | Documentation, requirements, design, testing, and acceptance materials | `<MODULE_DOCS_GIT_URL>` | `<MODULE_DOCS_BRANCH>` |
| `<MODULE_DEPLOY>` | `<MODULE_DEPLOY_PATH>` | Deployment scripts, images, seed data, and environment configuration | `<MODULE_DEPLOY_GIT_URL>` | `<MODULE_DEPLOY_BRANCH>` |

## Collaboration Rules

- Module sessions edit only their own module by default.
- Cross-module API, field, event, database, or configuration changes must be written to `dev-doc/` first.
- After each substantive session, module sessions update `memory-bank/module-<MODULE_NAME>-status.md`.
- The orchestrator session periodically summarizes `memory-bank/*status.md` and checks for conflicts and priorities.
- The root repository maintains orchestration files, rules, documentation, and submodule pointers. It should not mix in child module implementation code.
- If the user requests cross-module implementation, split the work first and route each task to the relevant module session.

## Worktree Rules

- Use Git worktrees for long-running or parallel tasks.
- Suggested branch prefixes: `codex/<task-slug>`, `cursor/<task-slug>`, `cline/<task-slug>`, `kiro/<task-slug>`.
- Put worktrees under a `worktrees/` directory next to the root project.
- One worktree should serve one task or one short-lived objective.

## Status Files

- Orchestrator status: `memory-bank/orchestrator-status.md`
- Module status: `memory-bank/module-<MODULE_NAME>-status.md`
- Current focus: `memory-bank/activeContext.md`
- Overall progress: `memory-bank/progress.md`
