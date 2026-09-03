# AI Workspace Kit

A workspace kit for managing AI coding-agent context across complex repositories. It helps Codex, Cursor, Cline, Kiro, and similar tools work from the same project context while respecting module boundaries.

[Chinese version](README_zh.md)

Use it when you want AI coding tools to recover after context resets, coordinate cross-module changes, and avoid scattering project state across chat history.

## What It Provides

- Root-level `memory-bank/` for project facts, active context, progress, and module status.
- `AGENTS.md`, `.cursor/rules/`, `.clinerules/`, and `.kiro/` templates for common AI coding tools.
- Module boundary rules for monorepos, multi-repo workspaces, submodules, and worktrees.
- `dev-doc/` for cross-module contracts before implementation.
- Optional role prompts for product, architecture, development, algorithm, UI/UX, agent, and QA work.

The Memory Bank pattern is based on Cline's Memory Bank: `https://docs.cline.bot/best-practices/memory-bank`.

## Layout

```text
<ROOT_PROJECT>/
  AGENTS.md
  .ai-control.yaml
  .aiignore
  .cursorignore
  .clineignore
  .cursor/rules/
  .clinerules/
  .ai-rules/roles/
  memory-bank/
    projectbrief.md
    productContext.md
    systemPatterns.md
    techContext.md
    activeContext.md
    progress.md
    orchestrator-status.md
    module-<MODULE_NAME>-status.md
  dev-doc/
  <MODULE_A>/
    AGENTS.md
    .cursor/
    .clinerules/
    .codex/
    .kiro/
```

## Quick Start

1. Copy this repository into your project root:

```text
my-new-project/
  ai-workspace-kit/
```

2. Open Codex, Cursor, Cline, or Kiro in the project root.

3. Ask the AI tool to initialize the kit:

```text
Please enable ai-workspace-kit for this project.

Read:
- ai-workspace-kit/README.md
- ai-workspace-kit/CHECKLIST.md
- ai-workspace-kit/prompts/00-bootstrap-root-project.md
- ai-workspace-kit/prompts/01-init-memory-bank.md
- ai-workspace-kit/prompts/02-add-submodules.md
- ai-workspace-kit/prompts/09-init-standalone-module-ai-rules.md
- ai-workspace-kit/prompts/10-init-ai-roles.md

Then create or update the root AI control files, root memory-bank, dev-doc, role rules, and module-level rules where useful.
Reuse existing files where possible. Do not overwrite important project files. Use TODO for missing facts.
Keep memory-bank root-only.
```

If you already know the modules, include them:

```text
Root project name: my-new-project
Project description: ...

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
```

## Core Rules

- Keep `memory-bank/` in the root project.
- Do not create separate module-level Memory Banks.
- Document cross-module API, schema, event, database, and config changes in root `dev-doc/` first.
- Module sessions should edit only their own module by default.
- After meaningful work, update the relevant root Memory Bank files.

## Common Prompts

- `prompts/00-bootstrap-root-project.md`: initialize root AI control files.
- `prompts/01-init-memory-bank.md`: initialize the root Memory Bank.
- `prompts/02-add-submodules.md`: add or register modules.
- `prompts/03-open-module-work.md`: start module work.
- `prompts/04-orchestrator-summary.md`: summarize root/module status.
- `prompts/05-create-worktree-task.md`: create a worktree task.
- `prompts/06-cross-module-contract.md`: write a cross-module contract.
- `prompts/07-session-handoff.md`: prepare a session handoff.
- `prompts/09-init-standalone-module-ai-rules.md`: add lightweight module rules.
- `prompts/10-init-ai-roles.md`: initialize role rules.
- `prompts/11-update-memory-bank.md`: update project context.
- `prompts/12-follow-custom-instructions.md`: recover context in a new session.

## Roles

```text
@pm          requirements, workflows, acceptance criteria
@architect   architecture, boundaries, contracts
@dev         implementation, APIs, data models
@algorithm   models, training, inference, evaluation
@uiux        screens, interaction, usability
@agent       tools, MCP, agent orchestration
@qa          test plans, regression, acceptance
```
