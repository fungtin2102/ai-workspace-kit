# AI Workspace Kit

A portable Memory Bank and AI agent workflow template for complex software projects. It helps teams coordinate Codex, Cursor, Cline, Kiro, and other AI coding agents across multi-repo workspaces, monorepos, Git submodules, Git worktrees, polyglot services, and long-running development sessions.

[Chinese version](README_zh.md)

Use it when you want AI coding tools to share project context, respect module boundaries, recover after context resets, and coordinate cross-module changes through a root-level Memory Bank.

Supported tools:
- Codex: use root and module `AGENTS.md` files to define operating boundaries.
- Cursor: use `.cursor/rules/` for project rules.
- Cline: use `.clinerules/` and `memory-bank/` for persistent context.
- Kiro: use `.kiro/`, `.clinerules/`, and startup prompts for context loading.

Origin:
- The single-repository memory pattern is based on Cline's Memory Bank: `https://docs.cline.bot/best-practices/memory-bank`.
- This template extends that pattern with root-level orchestration, module status files, Git submodules, Git worktrees, AI roles, and cross-module contracts.

## Keywords

`ai coding agent`, `memory bank`, `cline memory bank`, `codex agents.md`, `cursor rules`, `cline rules`, `kiro`, `multi-agent workflow`, `multi-repo`, `monorepo`, `git submodule`, `git worktree`, `polyglot repository`, `agentic coding`, `AI project template`, `developer workflow`, `context management`

Suggested GitHub repository description:

```text
Memory Bank and AI agent workflow kit for Codex, Cursor, Cline, and Kiro across monorepos, multi-repo workspaces, submodules, and worktrees.
```

Suggested GitHub topics:

```text
ai-agents, coding-agents, memory-bank, cline, codex, cursor, kiro, monorepo, multi-repo, git-submodules, git-worktrees, agentic-coding, developer-tools
```

## Who This Is For

- Teams using multiple AI coding tools in the same project.
- Projects split across backend, frontend, workers, AI services, deployment, and docs.
- Repositories that use Git submodules, worktrees, or multiple long-running branches.
- Developers who want Cline-style Memory Bank context management for larger multi-module workspaces.
- Teams that need AI agents to update shared project state instead of relying on chat history.

## Contents

- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [Recommended Layout](#recommended-layout)
- [How To Start](#how-to-start)
- [Git Submodules](#git-submodules)
- [Git Worktrees](#git-worktrees)
- [Standalone Module Sessions](#standalone-module-sessions)
- [AI Roles](#ai-roles)

## What This Solves

Complex projects often have these problems:
- The root repository coordinates work while implementation lives in multiple child repositories.
- Frontend, backend, AI, workers, deployment, and documentation may use different languages and stacks.
- Multiple AI tools may work in different sessions and accidentally edit across module boundaries.
- Long conversations lose context unless project state is written down.
- Submodules, worktrees, and parallel branches can become hard to coordinate.

This template uses:
- A root repository as the orchestrator workspace.
- Git submodules to mount implementation repositories.
- Git worktrees to isolate parallel tasks.
- A root-only `memory-bank/` as the single source of truth for project context for AI tools.
- Root and module `AGENTS.md` files to define edit boundaries.
- `dev-doc/` for cross-module contracts before implementation.
- AI role rules for `@architect`, `@pm`, `@dev`, `@algorithm`, `@uiux`, `@agent`, and `@qa`.

## How It Works

The template adds a lightweight coordination layer to your repository. The root project owns shared context, tool rules, role definitions, and cross-module agreements. Each module owns its implementation code and a small set of local AI rules.

At the start of a task, the AI reads the root rules and the root Memory Bank. If the task belongs to a module, it also reads that module's `AGENTS.md` and module status file. This gives the AI enough context to continue work without depending on chat history.

During work, cross-module changes go to `dev-doc/` first. This keeps API, data, event, and configuration agreements visible before separate module sessions implement them.

After substantive work, the AI updates the root Memory Bank, especially `activeContext.md`, `progress.md`, and `module-<MODULE_NAME>-status.md`. The next AI session can then recover the project state with the same instructions.

## Recommended Layout

```text
<ROOT_PROJECT>/
  AGENTS.md
  .ai-control.yaml
  .aiignore
  .cursorignore
  .clineignore
  .gitmodules
  .cursor/
    rules/
      00-project-rules.mdc
      memory-bank-protocol.mdc
      init-memory-bank.md
      roles.mdc
  .clinerules/
    README.md
    memory-bank-protocol.md
    init-memory-bank.md
    roles.md
  .ai-rules/
    roles/
      README.md
      architect.md
      pm.md
      dev.md
      algorithm.md
      uiux.md
      agent.md
      qa.md
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
    README.md
  <MODULE_A>/
    AGENTS.md
    .cursor/              # Optional: recommended when the module is opened alone.
      rules/
    .clinerules/          # Optional: recommended when the module is opened alone.
    .codex/               # Optional: module-level Codex notes.
    .kiro/                # Optional: module-level Kiro notes.
  <MODULE_B>/
    AGENTS.md
```

## Quick Start

This flow is intentionally similar to Cline's Memory Bank quick setup: copy the instructions into your project, then ask the AI to initialize the memory system.

1. Copy this directory into the new project root:

```text
my-new-project/
  ai-workspace-kit/
```

2. Open Codex, Cursor, Cline, or Kiro in the new project root.

3. Paste this prompt into the AI tool:

```text
Please enable the ai-workspace-kit multi-module AI collaboration system for the current project.

First read:
- ai-workspace-kit/README.md
- ai-workspace-kit/CHECKLIST.md
- ai-workspace-kit/AUDIT.md
- ai-workspace-kit/prompts/00-bootstrap-root-project.md
- ai-workspace-kit/prompts/01-init-memory-bank.md
- ai-workspace-kit/prompts/02-add-submodules.md
- ai-workspace-kit/prompts/09-init-standalone-module-ai-rules.md
- ai-workspace-kit/prompts/10-init-ai-roles.md
- ai-workspace-kit/prompts/11-update-memory-bank.md
- ai-workspace-kit/prompts/12-follow-custom-instructions.md

Then initialize the following based on the current project state:
- AGENTS.md
- .ai-control.yaml
- .aiignore
- .cursorignore
- .clineignore
- .cursor/rules/
- .clinerules/
- .ai-rules/roles/
- memory-bank/
- dev-doc/

If this project already has submodules, module directories, or a .gitmodules file, detect and reuse them. Do not overwrite important existing files.
If modules may be developed in standalone AI sessions, add lightweight module rules: AGENTS.md, .cursor/rules/, .clinerules/, .codex/, and .kiro/.
Important: keep memory-bank root-only. Do not create a second memory-bank inside modules. Standalone module sessions must read and update the root memory-bank.
If project information is missing, write TODO entries instead of inventing facts.
Finally output: files created or updated, information still needed, and recommended next steps.
```

4. If you already know the module list, paste it together with the prompt:

```text
Root project name: my-new-project
Project description: Write the project description here.

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
- deploy: path deploy, Git URL <url>, branch main, responsibility deployment scripts
- docs: path docs, Git URL <url>, branch main, responsibility project documentation
```

The AI can then generate the root rules, Memory Bank, role rules, module instructions, and optional standalone module rules. In most projects, the only information you need to confirm is:
- Root project name.
- Module list.
- Paths AI tools should not read.

## How To Start

Use the Quick Start when you want the lowest-friction path. Use the steps below when you want to understand or adjust each part of the setup.

Each step includes:
- Manual or semi-manual setup.
- An AI-assisted shortcut.
- How to adjust it later.

### Step 1: Add The Template

Manual or semi-manual:
- Copy `ai-workspace-kit/` into the root of your target project.
- If the target project is not a Git repository yet, initialize it:

```bash
git init <ROOT_PROJECT>
cd <ROOT_PROJECT>
```

AI-assisted shortcut:

```text
I copied ai-workspace-kit into this repository. Please inspect the template and tell me what project information you need before enabling it.
```

Adjust later:

```text
Please review the AI template setup and tell me whether any generated files are missing or outdated. Do not modify implementation code.
```

### Step 2: Create The Root Control Layer

Manual or semi-manual:
- Copy `templates/root-AGENTS.md` to `AGENTS.md`.
- Copy `templates/config/project-ai-control.yaml` to `.ai-control.yaml`.
- Copy ignore templates from `templates/ignore/`.
- Replace placeholders such as `<ROOT_PROJECT>`, `<ROOT_PROJECT_PATH>`, and `<ROOT_BRANCH>`.

AI-assisted shortcut:

```text
Please initialize the root AI control layer using ai-workspace-kit/prompts/00-bootstrap-root-project.md. Reuse existing files where possible, merge with existing rules, and use TODO for missing facts.
```

Adjust later:

```text
Please update the root AI control files after this project rename: root project is <ROOT_PROJECT>, root path is <ROOT_PROJECT_PATH>, default branch is <ROOT_BRANCH>. Keep memory-bank root-only.
```

### Step 3: Initialize The Root Memory Bank

Manual or semi-manual:
- Copy `templates/memory-bank/` to `memory-bank/`.
- Create one `memory-bank/module-<MODULE_NAME>-status.md` per module.
- Keep Memory Bank in the root project. Do not create module-level Memory Banks.

AI-assisted shortcut:

```text
Please initialize the root Memory Bank using ai-workspace-kit/prompts/01-init-memory-bank.md. Detect existing modules where possible. Use TODO for unknown information and do not create memory-bank directories inside modules.
```

Adjust later:

```text
Please run update memory bank using ai-workspace-kit/prompts/11-update-memory-bank.md. Review the six core files and the relevant module status files, then update only facts that changed.
```

### Step 4: Add Or Register Modules

Manual or semi-manual:
- If modules already have Git repositories, add them as submodules:

```bash
git submodule add -b <MODULE_BRANCH> <MODULE_GIT_URL> <MODULE_PATH>
git submodule update --init --recursive
```

- If modules are just directories for now, register them in `.ai-control.yaml`, `AGENTS.md`, and `memory-bank/projectbrief.md`.
- Create one module status file in root Memory Bank for each module.

AI-assisted shortcut:

```text
Please add or register my modules using ai-workspace-kit/prompts/02-add-submodules.md.

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
- docs: path docs, Git URL <url>, branch main, responsibility documentation
```

Adjust later:

```text
Please add a new module named <MODULE_NAME> at <MODULE_PATH>. Its Git URL is <MODULE_GIT_URL>, branch is <MODULE_BRANCH>, and responsibility is <MODULE_DESCRIPTION>. Update AGENTS.md, .ai-control.yaml, .gitmodules if needed, and root memory-bank status files.
```

### Step 5: Add Module-Level Rules For Standalone Sessions

Manual or semi-manual:
- For modules that may be opened alone, copy lightweight rules:

```text
templates/module-level/AGENTS.md              -> <MODULE_PATH>/AGENTS.md
templates/module-level/.cursor/               -> <MODULE_PATH>/.cursor/
templates/module-level/.clinerules/           -> <MODULE_PATH>/.clinerules/
templates/module-level/.codex/                -> <MODULE_PATH>/.codex/
templates/module-level/.kiro/                 -> <MODULE_PATH>/.kiro/
templates/module-level/dev-doc-README.md      -> <MODULE_PATH>/dev-doc/README.md
```

- These files should point back to the root project for `memory-bank/` and `dev-doc/`.

AI-assisted shortcut:

```text
Please enable standalone AI sessions for <MODULE_NAME> using ai-workspace-kit/prompts/09-init-standalone-module-ai-rules.md. The root project path is <ROOT_PROJECT_PATH>. Do not create a module-level memory-bank.
```

Adjust later:

```text
Please update the standalone module rules for <MODULE_NAME>. This module should still write status to <ROOT_PROJECT_PATH>/memory-bank/module-<MODULE_NAME>-status.md and cross-module contracts to <ROOT_PROJECT_PATH>/dev-doc/.
```

### Step 6: Add AI Roles

Manual or semi-manual:
- Copy `templates/roles/` to `.ai-rules/roles/`.
- Copy `templates/cursor-rules/roles/roles.mdc` to `.cursor/rules/roles.mdc`.
- Copy `templates/clinerules/roles/roles.md` to `.clinerules/roles.md`.
- Adjust role-to-module mappings for your project.

AI-assisted shortcut:

```text
Please initialize AI role rules using ai-workspace-kit/prompts/10-init-ai-roles.md. Map roles to the modules in this project and keep the root Memory Bank as the only project state source.
```

Adjust later:

```text
Please adjust the role rules: @algorithm should own <MODULE_PATH>, @uiux should own <MODULE_PATH>, and @qa should include regression checks for <MODULE_PATH>. Update .ai-rules/roles/, .cursor/rules/roles.mdc, and .clinerules/roles.md.
```

### Step 7: Start Daily Work

Manual or semi-manual:
- Start orchestrator work from the root project.
- Start module work from the module directory.
- Read the relevant prompt from `prompts/` before starting.

AI-assisted shortcut:

```text
Please recover context using ai-workspace-kit/prompts/12-follow-custom-instructions.md, then continue this task:

<TASK_DESCRIPTION>
```

Adjust later:

```text
Please summarize current module status, update the root Memory Bank, and suggest the next three tasks for the orchestrator session.
```

### Step 8: Use Worktrees For Parallel Work

Manual or semi-manual:
- Create one worktree per parallel task.
- Use a clear branch prefix such as `codex/`, `cursor/`, `cline/`, or `kiro/`.

AI-assisted shortcut:

```text
Please create a worktree for this parallel task using ai-workspace-kit/prompts/05-create-worktree-task.md.

Module: <MODULE_NAME>
Base branch: <BASE_BRANCH>
Task slug: <TASK_SLUG>
Task: <TASK_DESCRIPTION>
```

Adjust later:

```text
Please review active worktrees, update the relevant module status files in root memory-bank, and identify which worktrees are ready to merge or remove.
```

## Git Submodules

The root repository records submodule pointers and global collaboration files. Implementation code stays in child repositories.

Common commands:

```bash
git submodule status --recursive
git submodule update --init --recursive
git submodule foreach 'git status --short'
git submodule foreach 'git branch --show-current'
```

Add a module:

```bash
git submodule add -b <MODULE_BRANCH> <MODULE_GIT_URL> <MODULE_PATH>
```

Update the root pointer for a module:

```bash
cd <MODULE_PATH>
git checkout <MODULE_BRANCH>
git pull --ff-only
cd ..
git add <MODULE_PATH> .gitmodules
git commit -m "chore: update <MODULE_NAME> submodule"
```

## Git Worktrees

Use worktrees for long-running or parallel tasks in the same module.

Suggested layout:

```text
../worktrees/
  <ROOT_PROJECT>-<MODULE_NAME>-<TASK_SLUG>/
```

Create a worktree:

```bash
cd <ROOT_PROJECT>/<MODULE_PATH>
git fetch
git worktree add ../../worktrees/<ROOT_PROJECT>-<MODULE_NAME>-<TASK_SLUG> -b codex/<TASK_SLUG> origin/<MODULE_BRANCH>
```

Inspect worktrees:

```bash
git worktree list
```

Remove a completed worktree:

```bash
git worktree remove ../../worktrees/<ROOT_PROJECT>-<MODULE_NAME>-<TASK_SLUG>
git branch -d codex/<TASK_SLUG>
```

## Multi-Session AI Collaboration

Recommended sessions:
- Orchestrator session: open the root repository; split tasks, summarize state, and maintain cross-module contracts.
- Module session: open a module directory; work only inside that module.
- Documentation session: open `dev-doc/` or the formal docs module; maintain requirements, design, testing, deployment, and acceptance materials.

Required rules:
- A module session edits only its own module by default.
- Cross-module API, field, event, database, or configuration changes must be documented in root `dev-doc/` first.
- Significant work must update `memory-bank/module-<MODULE_NAME>-status.md`.
- The orchestrator session periodically summarizes `memory-bank/*status.md`.

## Standalone Module Sessions

If modules are often opened alone, add lightweight AI files to each module:

```text
<MODULE_PATH>/
  AGENTS.md
  .cursor/rules/
  .clinerules/
  .codex/
  .kiro/
  dev-doc/               # Optional: points back to root dev-doc.
```

Context lookup:
1. If the parent root exists, read `../AGENTS.md`, `../memory-bank/`, and `../dev-doc/`.
2. If the module is an independent clone, ask for `<ROOT_PROJECT_PATH>` or ask the user to add the root project to the same workspace.
3. Do not maintain a second module-level `memory-bank/`.

Status updates:
1. Root checkout mode: update `../memory-bank/module-<MODULE_NAME>-status.md`.
2. Standalone module mode: update `<ROOT_PROJECT_PATH>/memory-bank/module-<MODULE_NAME>-status.md`.
3. If the root Memory Bank cannot be located, stop and ask for its path.

## Files

- `templates/root-AGENTS.md`: root orchestrator instructions.
- `templates/module-AGENTS.md`: module session instructions.
- `templates/module-level/`: lightweight rules for modules opened alone.
- `templates/gitmodules.template`: `.gitmodules` template.
- `templates/config/project-ai-control.yaml`: project AI control manifest.
- `templates/ignore/`: `.aiignore`, `.cursorignore`, and `.clineignore` templates.
- `templates/cursor-rules/`: Cursor rule templates.
- `templates/clinerules/`: Cline/Kiro rule templates.
- `templates/roles/`: AI role templates.
- `templates/memory-bank/`: root Memory Bank templates.
- `prompts/`: ready-to-use prompts for initialization, task routing, handoff, and recovery.
- `AUDIT.md`: completeness check against the original Cline Memory Bank pattern.
- `EXAMPLE_PROJECT_EXPORT.md`: generic example project configuration.

## Recommended Initialization Order

1. Run `prompts/00-bootstrap-root-project.md` to create the root control layer.
2. Run `prompts/01-init-memory-bank.md` to initialize root memory.
3. Run `prompts/02-add-submodules.md` to add or register modules.
4. Run `prompts/09-init-standalone-module-ai-rules.md` for modules opened independently.
5. Run `prompts/10-init-ai-roles.md` to initialize role rules.
6. Use `prompts/12-follow-custom-instructions.md` to resume context in new sessions.
7. Use `prompts/03-open-module-work.md` to start module work.
8. Use `prompts/04-orchestrator-summary.md` for periodic root summaries.
9. Use `prompts/11-update-memory-bank.md` before milestones or context switches.

## AI Roles

| Role | Trigger | Best For |
|------|---------|----------|
| Architect | `@architect` | Architecture, module boundaries, technical decisions |
| Product Manager | `@pm` | Requirements, workflows, acceptance criteria, priorities |
| Developer | `@dev` | Implementation, APIs, data models, integration |
| Algorithm Engineer | `@algorithm` | Models, training, inference, evaluation, datasets |
| UI/UX Engineer | `@uiux` | Screens, interaction, visual hierarchy, usability |
| Agent Engineer | `@agent` | Tools, MCP, plugins, agent orchestration, streaming events |
| QA Engineer | `@qa` | Test plans, test cases, regression, security, acceptance |

Usage examples:

```text
@pm Turn this idea into user stories and acceptance criteria.
@architect Design the module boundaries and interface contracts.
@dev Implement this API in the backend module.
@algorithm Design the training and inference workflow.
@uiux Improve the information architecture of this configuration screen.
@agent Design the tool-calling flow for this copilot.
@qa Generate test cases from the dev-doc contract.
```

## Notes

- Do not use deprecated or archived directories as implementation references.
- Do not let one AI session make broad edits across many modules unless the task is small and explicit.
- Do not rely on chat history for long-term state; write important state into root `memory-bank/`.
- Do not scatter temporary cross-module agreements inside implementation code; write them in root `dev-doc/` first.
