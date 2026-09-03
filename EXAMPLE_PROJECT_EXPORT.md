# Example Project Export

This is a generic example that shows how to fill in a complex multi-project setup. It is safe to publish as long as you do not replace the placeholders with private project names, private Git URLs, organization names, or personal paths.

## Root Project

- Root project name: `example-platform-all`
- Root path: `/path/to/example-platform-all`
- Root session role: orchestrator session for orchestration, task splitting, status summaries, and cross-module contracts.

## AI Rule Entry Points

Root directory:
- `AGENTS.md`: Codex orchestrator rules.
- `.cursor/rules/`: Cursor rules.
- `.clinerules/`: Cline rules.
- `.ai-rules/roles/`: shared role rules.
- `memory-bank/`: single source of truth for cross-tool and cross-session project state.
- `dev-doc/`: cross-module contracts, draft designs, and integration notes.

Module directories:
- `<module>/AGENTS.md`: module-specific Codex rules.
- `<module>/.cursor/rules/`: optional module-level Cursor rules.
- `<module>/.clinerules/`: optional module-level Cline rules.
- `<module>/.codex/`: optional module-level Codex notes.
- `<module>/.kiro/`: optional module-level Kiro notes.

## Ignore Rules

Example forbidden or low-value directories:
- `archive/`
- `legacy/`
- `node_modules/`
- `dist/`
- `build/`
- `target/`
- `.venv/`

## Memory Bank Files

Core files:
- `memory-bank/projectbrief.md`
- `memory-bank/productContext.md`
- `memory-bank/systemPatterns.md`
- `memory-bank/techContext.md`
- `memory-bank/activeContext.md`
- `memory-bank/progress.md`

Multi-module status files:
- `memory-bank/orchestrator-status.md`
- `memory-bank/module-backend-status.md`
- `memory-bank/module-frontend-status.md`
- `memory-bank/module-gateway-status.md`
- `memory-bank/module-worker-status.md`
- `memory-bank/module-deploy-status.md`
- `memory-bank/module-docs-status.md`

Optional topic memory files:
- `memory-bank/api-contracts.md`
- `memory-bank/integration-notes.md`
- `memory-bank/session-handoff.md`
- `memory-bank/backlog.md`

## Submodule Example

```ini
[submodule "backend"]
	path = backend
	url = https://github.com/example-org/backend.git
	branch = main

[submodule "frontend"]
	path = frontend
	url = https://github.com/example-org/frontend.git
	branch = main

[submodule "gateway"]
	path = gateway
	url = https://github.com/example-org/gateway.git
	branch = main

[submodule "worker"]
	path = worker
	url = https://github.com/example-org/worker.git
	branch = main

[submodule "deploy"]
	path = deploy
	url = https://github.com/example-org/deploy.git
	branch = main

[submodule "docs"]
	path = docs
	url = https://github.com/example-org/docs.git
	branch = main
```

## Example Module Responsibilities

| Module | Responsibility |
|--------|----------------|
| `backend` | Backend APIs, business services, data access, authorization, integrations |
| `frontend` | Web UI, screens, components, interaction experience |
| `gateway` | Service gateway, BFF, AI/agent orchestration, streaming APIs |
| `worker` | Background jobs, batch processing, model inference, async tasks |
| `deploy` | Docker, Kubernetes, deployment scripts, seed data |
| `docs` | Requirements, design, testing, deployment, and acceptance documentation |

## Collaboration Summary

- The root session acts as the orchestrator and focuses on coordination rather than implementation.
- Module sessions edit only their own directories by default.
- Cross-module agreements are written to root `dev-doc/` first.
- After each substantive work session, update root `memory-bank/module-*-status.md`.
- The orchestrator session periodically summarizes `memory-bank/*status.md`.
- Modules may have lightweight local AI rules, but they do not maintain a second `memory-bank/`.

## Standalone Module Sessions

If Cursor, Cline, Kiro, or Codex may open modules independently, add lightweight rule files to each module while keeping `memory-bank/` root-only:

```text
<MODULE>/
  AGENTS.md
  .cursor/rules/
  .clinerules/
  .codex/
  .kiro/
  dev-doc/     # Optional: points back to root dev-doc.
```

Standalone module sessions must read and update the root `memory-bank/`. If the root path cannot be found, the AI should ask the user for the root path or ask the user to add the root project to the workspace. Do not create a second module-level Memory Bank.
