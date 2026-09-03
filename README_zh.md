# AI Workspace Kit

[English](README.md)

这是一套用于管理 AI coding-agent 项目上下文的工作区模板，适合结构较复杂的代码仓库。它帮助 Codex、Cursor、Cline、Kiro 等工具在同一套项目上下文下工作，同时遵守模块边界。

适用于需要在上下文重置后恢复工作、协调跨模块变更，并避免把长期项目状态散落在聊天记录里的工程。

## 提供什么

- 根工程 `memory-bank/`：记录项目事实、当前上下文、进度和模块状态。
- `AGENTS.md`、`.cursor/rules/`、`.clinerules/`、`.kiro/`：适配常见 AI coding tools。
- 模块边界规则：适用于 monorepo、multi-repo workspace、submodule 和 worktree。
- `dev-doc/`：先记录跨模块契约，再进入实现。
- 可选角色规则：覆盖产品、架构、开发、算法、UI/UX、Agent 和 QA 工作。

Memory Bank 模式参考 Cline 官方文档：`https://docs.cline.bot/best-practices/memory-bank`

## 目录结构

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

## 快速开始

1. 把本仓库复制到目标工程根目录：

```text
my-new-project/
  ai-workspace-kit/
```

2. 在目标工程根目录打开 Codex、Cursor、Cline 或 Kiro。

3. 让 AI 初始化：

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

如果已经知道模块清单，可以一起提供：

```text
Root project name: my-new-project
Project description: ...

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
```

## 核心约定

- `memory-bank/` 保持在根工程。
- 子模块不要维护第二套 Memory Bank。
- 跨模块 API、字段、事件、数据库、配置变更先写入根工程 `dev-doc/`。
- 模块会话默认只修改自己的模块。
- 完成实质性工作后，更新相关的根工程 Memory Bank 文件。

## 常用 Prompt

- `prompts/00-bootstrap-root-project.md`：初始化根工程控制文件。
- `prompts/01-init-memory-bank.md`：初始化根 Memory Bank。
- `prompts/02-add-submodules.md`：添加或登记模块。
- `prompts/03-open-module-work.md`：启动模块工作。
- `prompts/04-orchestrator-summary.md`：汇总根工程和模块状态。
- `prompts/05-create-worktree-task.md`：创建 worktree 任务。
- `prompts/06-cross-module-contract.md`：编写跨模块契约。
- `prompts/07-session-handoff.md`：准备会话交接。
- `prompts/09-init-standalone-module-ai-rules.md`：添加子模块轻量规则。
- `prompts/10-init-ai-roles.md`：初始化角色规则。
- `prompts/11-update-memory-bank.md`：更新项目上下文。
- `prompts/12-follow-custom-instructions.md`：在新会话中恢复上下文。

## 角色

```text
@pm          requirements, workflows, acceptance criteria
@architect   architecture, boundaries, contracts
@dev         implementation, APIs, data models
@algorithm   models, training, inference, evaluation
@uiux        screens, interaction, usability
@agent       tools, MCP, agent orchestration
@qa          test plans, regression, acceptance
```
