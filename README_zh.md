# AI Workspace Kit

[English](README.md)

这是一套可迁移的 Memory Bank 与 AI agent 工作流模板，适用于复杂软件工程。它帮助团队在 multi-repo workspace、monorepo、Git submodule、Git worktree、多语言服务和长期开发会话中协调 Codex、Cursor、Cline、Kiro 以及其他 AI coding agents。

当你希望 AI 编程工具共享项目上下文、遵守模块边界、在上下文重置后恢复工作，并通过根工程 Memory Bank 协调跨模块变更时，可以使用这套模板。

支持工具：
- Codex：通过根目录和模块目录的 `AGENTS.md` 定义工作边界。
- Cursor：通过 `.cursor/rules/` 读取项目规则。
- Cline：通过 `.clinerules/` 和 `memory-bank/` 维护跨会话上下文。
- Kiro：通过 `.kiro/`、`.clinerules/` 和启动 Prompt 加载上下文。

设计来源：
- 单仓库记忆模式参考 Cline 官方 Memory Bank：`https://docs.cline.bot/best-practices/memory-bank`
- 本模板在此基础上增加了根工程编排、模块状态文件、Git submodule、Git worktree、AI 角色和跨模块契约。

## Keywords

`ai coding agent`, `memory bank`, `cline memory bank`, `codex agents.md`, `cursor rules`, `cline rules`, `kiro`, `multi-agent workflow`, `multi-repo`, `monorepo`, `git submodule`, `git worktree`, `polyglot repository`, `agentic coding`, `AI project template`, `developer workflow`, `context management`

## 适合谁

- 同一个项目里同时使用多个 AI coding tools 的团队。
- 项目拆分为 backend、frontend、workers、AI services、deployment、docs 等多个模块。
- 使用 Git submodules、worktrees 或多个长期分支的仓库。
- 想把 Cline-style Memory Bank 扩展到大型多模块工作区的开发者。
- 希望 AI agents 更新共享项目状态，而不是依赖聊天记录的团队。

## 目录

- [快速开始](#快速开始)
- [工作原理](#工作原理)
- [适合谁](#适合谁)
- [推荐目录结构](#推荐目录结构)
- [跨工具生效方式](#跨工具生效方式)
- [核心约定](#核心约定)
- [常用 Prompt](#常用-prompt)
- [角色](#角色)

## 解决什么问题

复杂工程常见问题：
- 根仓库负责组织协调，真正实现分布在多个子仓库。
- 前端、后端、AI、Worker、部署、文档可能使用不同语言和技术栈。
- 多个 AI 工具在不同会话中工作，容易跨模块误改。
- 长会话结束后，如果不写入项目状态，AI 很难继续上下文。
- Submodule、worktree、并行分支不容易统一管理。

本模板提供：
- 根工程作为 orchestrator workspace。
- Git submodule 挂载各实现仓库。
- Git worktree 隔离并行任务。
- 根工程唯一 `memory-bank/`，作为 AI 工具可读取的项目上下文事实源。
- 根目录和模块目录的 `AGENTS.md` 定义编辑边界。
- `dev-doc/` 用于先写跨模块契约，再做实现。
- `@architect`、`@pm`、`@dev`、`@algorithm`、`@uiux`、`@agent`、`@qa` 角色规则。

## 工作原理

这套模板会在你的仓库里增加一层轻量协作控制层。根工程负责共享上下文、工具规则、角色定义和跨模块约定；每个子模块负责自己的实现代码，并保留少量本地 AI 规则。

任务开始时，AI 先读取根工程规则和根工程 Memory Bank。如果任务属于某个子模块，AI 还会读取该模块的 `AGENTS.md` 和模块状态文件。这样 AI 不依赖历史聊天记录，也能继续理解项目状态。

开发过程中，跨模块变更先写入 `dev-doc/`。API、数据结构、事件、配置等约定先被记录下来，再交给不同模块会话分别实现。

完成实质性工作后，AI 会更新根工程 Memory Bank，尤其是 `activeContext.md`、`progress.md` 和 `module-<MODULE_NAME>-status.md`。下一个 AI 会话可以用同一套启动指令恢复上下文。

## 推荐目录结构

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
  .clinerules/
  .ai-rules/
    roles/
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
    .cursor/
    .clinerules/
    .codex/
    .kiro/
```

## 快速开始

这个流程参考了 Cline Memory Bank 的快速入门方式：把指令放进项目，然后让 AI 初始化记忆系统。

1. 把模板目录复制到新工程根目录：

```text
my-new-project/
  ai-workspace-kit/
```

2. 在新工程根目录打开 Codex / Cursor / Cline / Kiro。

3. 复制下面这段给 AI：

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

4. 如果你已经知道子模块清单，可以一起贴给 AI：

```text
Root project name: my-new-project
Project description: Write the project description here.

Modules:
- backend: path backend, Git URL <url>, branch main, responsibility backend services
- frontend: path frontend, Git URL <url>, branch main, responsibility frontend application
- deploy: path deploy, Git URL <url>, branch main, responsibility deployment scripts
- docs: path docs, Git URL <url>, branch main, responsibility project documentation
```

AI 会自动生成根规则、Memory Bank、角色规则、模块指令，以及可选的子模块独立会话规则。通常你只需要确认三类信息：
- 根工程名。
- 子模块列表。
- AI 工具禁止读取的路径。

## 跨工具生效方式

- Codex：主要读取 `AGENTS.md`，模块 `AGENTS.md` 也会生效。
- Cursor：主要读取 `.cursor/rules/`。
- Cline：主要读取 `.clinerules/`。
- Kiro：可通过 `.kiro/`、`.clinerules/` 和启动 Prompt 生效。
- 通用角色：通过 `.ai-rules/roles/`、启动 Prompt、Cursor/Cline 入口文件生效。
- Memory Bank：Markdown 文件可被各工具读写，因此通用生效。

## 核心约定

- `memory-bank/` 尽量只在根工程维护。
- 子模块不要创建第二套 `memory-bank/`。
- 子模块独立打开时，也要读取和更新根工程 `memory-bank/`。
- 跨模块 API、字段、事件、数据库、配置变更，先写根工程 `dev-doc/`。
- 每次完成实质性工作后，更新根工程 `memory-bank/module-<MODULE_NAME>-status.md`。

## 常用 Prompt

- `prompts/00-bootstrap-root-project.md`：初始化根工程控制层。
- `prompts/01-init-memory-bank.md`：初始化根 Memory Bank。
- `prompts/02-add-submodules.md`：添加或识别 Git submodule。
- `prompts/03-open-module-work.md`：启动模块工作会话。
- `prompts/04-orchestrator-summary.md`：根工程 orchestrator 汇总。
- `prompts/05-create-worktree-task.md`：为并行任务创建 worktree。
- `prompts/06-cross-module-contract.md`：先写跨模块契约。
- `prompts/07-session-handoff.md`：会话交接。
- `prompts/08-kiro-cursor-codex-cline-universal-start.md`：通用启动 Prompt。
- `prompts/09-init-standalone-module-ai-rules.md`：给子模块启用独立会话轻量规则。
- `prompts/10-init-ai-roles.md`：初始化角色规则。
- `prompts/11-update-memory-bank.md`：更新 Memory Bank。
- `prompts/12-follow-custom-instructions.md`：恢复上下文。

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
