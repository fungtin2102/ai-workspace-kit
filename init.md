# Quick Initialization Prompt

1. Copy this directory into the new project root:

```text
my-new-project/
  ai-workspace-kit/
```

2. Open Codex, Cursor, Cline, or Kiro in the new project root.

3. Copy this prompt into the AI tool:

```text
Please enable the ai-workspace-kit multi-module AI collaboration system for the current project.

First read:
- ai-workspace-kit/README.md
- ai-workspace-kit/AUDIT.md
- ai-workspace-kit/CHECKLIST.md
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
If project information is missing, write `TODO` entries instead of inventing facts.
Finally output: files created or updated, information still needed, and recommended next steps.
```

If you already know the module list, include it:

```text
Root project name: my-new-project
Project description: Write the project description here.

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
- deploy: path deploy, Git URL <url>, branch main, responsibility deployment scripts
- docs: path docs, Git URL <url>, branch main, responsibility project documentation
```

Usually the user only needs to confirm three things: root project name, module list, and directories AI tools must not read.

Tool entry points:
- Codex: reads `AGENTS.md`; module `AGENTS.md` files also apply.
- Cursor: reads `.cursor/rules/`.
- Cline: reads `.clinerules/`.
- Kiro: can use `.kiro/`, `.clinerules/`, and startup prompts.
- Shared roles: use `.ai-rules/roles/` plus the startup prompts and Cursor/Cline role entry files.
- Memory Bank: Markdown files are readable and writable by all tools.
