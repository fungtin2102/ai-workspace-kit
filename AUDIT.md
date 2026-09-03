# Template Completeness Audit

Reference:
- Cline Memory Bank: `https://docs.cline.bot/best-practices/memory-bank`

## Compared With Cline's Single-Project Memory Bank

| Original capability | Template status | Notes |
|---------------------|-----------------|-------|
| `memory-bank/` Markdown context directory | Covered | Root-only single source of truth |
| `projectbrief.md` | Covered | Goals, scope, constraints, module list |
| `productContext.md` | Covered | Users, scenarios, workflows, UX goals |
| `activeContext.md` | Covered | Current focus, recent changes, next steps |
| `systemPatterns.md` | Covered | Architecture, module relationships, patterns |
| `techContext.md` | Covered | Stack, environment, commands, deployment constraints |
| `progress.md` | Covered | Done, todo, risks, milestones |
| `initialize memory bank` | Covered | `prompts/01-init-memory-bank.md` |
| `update memory bank` | Covered | `prompts/11-update-memory-bank.md` |
| `follow your custom instructions` | Covered | `prompts/12-follow-custom-instructions.md` |
| Cline Rules | Covered | `templates/clinerules/` |

## Multi-Project Extensions

| Extension | Status | Files |
|-----------|--------|-------|
| Root orchestrator session | Covered | `templates/root-AGENTS.md` |
| Module session rules | Covered | `templates/module-AGENTS.md` |
| Standalone module session rules | Covered | `templates/module-level/` |
| Root-only Memory Bank | Covered | README, module-level rules, prompts |
| Per-module status files | Covered | `templates/memory-bank/module-status.template.md` |
| Cross-module contract directory | Covered | `templates/dev-doc-README.md` |
| Git submodules | Covered | `templates/gitmodules.template`, Prompt 02 |
| Git worktrees | Covered | Prompt 05, README |
| AI roles | Covered | `templates/roles/`, Prompt 10 |
| Multi-tool entry points | Covered | Codex, Cursor, Cline, and Kiro rules |
| Ignore rules | Covered | `templates/ignore/` |
| Project control manifest | Covered | `templates/config/project-ai-control.yaml` |

## Information Users Must Provide

- Root project name, root Git URL, and default branch.
- Module names, paths, Git URLs, default branches, and responsibilities.
- Which modules may be opened or cloned independently.
- The root project absolute path for standalone module sessions.
- Forbidden-read directories and generated artifact directories.
- Dev, test, and build commands for each module.
- Role-to-module mappings.

## Suggested Initialization Order

1. Run Prompt 00 to initialize the root control layer.
2. Run Prompt 01 to initialize the root Memory Bank.
3. Run Prompt 10 to initialize role rules.
4. Run Prompt 02 to add or register submodules.
5. Run Prompt 09 for modules that may be developed independently.
6. Use Prompt 12 to resume context in daily sessions.
7. Use Prompt 11 or Prompt 07 before handoff or context switches.
