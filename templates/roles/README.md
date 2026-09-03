# AI Roles

This directory defines common AI roles for complex projects. Tools can activate these roles when the user explicitly uses `@architect`, `@pm`, `@dev`, `@algorithm`, `@uiux`, `@agent`, or `@qa`.

## Role Overview

| Role | Trigger | Core Responsibility | Typical Outputs |
|------|---------|---------------------|-----------------|
| Architect | `@architect` | Architecture, module boundaries, technical decisions, cross-module contracts | Architecture docs, ADRs, interface boundaries |
| Product Manager | `@pm` | Requirements, workflows, acceptance criteria, priority | PRDs, user stories, acceptance cases |
| Developer | `@dev` | Business code, APIs, data models, integrations | Code, migrations, tests, integration notes |
| Algorithm Engineer | `@algorithm` | AI/ML/CV/NLP, training, inference, evaluation | Model services, training scripts, evaluation reports |
| UI/UX Engineer | `@uiux` | Information architecture, interaction, visual hierarchy, usability | Screens, components, prototypes, usability notes |
| Agent Engineer | `@agent` | Tools, MCP, agent orchestration, conversation state, streaming | Tool schemas, orchestration logic, agent designs |
| QA Engineer | `@qa` | Test strategy, test cases, regression, security, acceptance | Test plans, bug reports, acceptance reports |

## Common Rules

- Use English by default.
- Read the root `memory-bank/` core files before starting work.
- Read the module `AGENTS.md` for module tasks.
- Write cross-module changes to root `dev-doc/` first.
- Update root `memory-bank/` after substantive work.
- Roles must not make broad edits outside their responsibility boundary. Split cross-module work first.

## Role Switching

Users can write:

```text
@pm Clarify this requirement.
@architect Design the module boundaries.
@dev Implement this change.
@qa Add tests and acceptance checks.
```

If no role is specified, choose the best role for the task and state it briefly.
