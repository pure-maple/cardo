# 在你的项目中使用 Meridian 协作框架

> 将多智能体协作体系引入任何项目——不限于软件开发，不绑定特定 AI 工具。

## 前提

你需要：
- 至少一个 AI CLI 工具（Claude Code、Codex、Gemini CLI、Cursor、或其他）

你**不需要**：
- 绑定某个特定 AI 工具——框架是工具无关的
- 安装 modelmux 或 Meridian——Cardo 是独立可用的

## 两种采纳方式

### 方式一：自动引导（推荐，需要 Claude Code）

将 Cardo 的采纳命令复制到你的项目中，然后运行：

```bash
# 复制采纳命令
mkdir -p ~/your-project/.claude/commands
cp cardo/commands/cardo-adopt.md ~/your-project/.claude/commands/

# 在项目目录下启动 Claude Code，然后运行：
/cardo-adopt
```

Cairn 会分析你的项目现状、检测现有 AI 框架、交互式引导设计 agent team、生成全套配置。

### 方式二：手动采纳

如果你不用 Claude Code，或者想完全手动控制，按以下步骤操作。

#### Step 1 — 创建 AGENTS.md（核心，工具无关）

`AGENTS.md` 是面向**所有 AI 工具**的协作指南。任何 CLI（Codex、Gemini、Claude Code、Cursor）都会读取项目根目录的 `AGENTS.md`。

在你的项目根目录创建 `AGENTS.md`：

```markdown
# 项目名 — Multi-Agent Collaboration Guide

> 所有 AI agent 在开始工作前请先读完此文件。

## 项目简介

（一段话说明项目是什么、用什么技术栈）

## Agent Team

| Name | Role | Scope |
|------|------|-------|
| _(register here)_ | | |

## Key Rules

- Never push directly to `main` — always PR workflow
- （你的项目特有规则）
```

#### Step 2 — 创建工具专属配置（按需）

不同 AI 工具有各自的配置文件，**按你实际使用的工具添加**：

| AI 工具 | 配置文件 | 作用 |
|---------|---------|------|
| Claude Code | `CLAUDE.md` | 角色体系、索引、硬约束 |
| Codex | `AGENTS.md`（已有） | Codex 原生支持 AGENTS.md |
| Cursor | `.cursor/rules/*.mdc` | Cursor rules |
| Windsurf | `.windsurfrules` | Windsurf 配置 |
| Gemini CLI | `GEMINI.md` 或 `AGENTS.md` | Gemini 配置 |

如果你**同时使用多个工具**，`AGENTS.md` 是唯一的跨工具共享层。工具专属配置可以引用它：

```markdown
# CLAUDE.md（Claude Code 专属）

参见 AGENTS.md 获取完整的协作规范。以下是 Claude Code 的额外配置：
- ...
```

#### Step 3 — 设计 Agent Team（使用 CORTEX）

使用 [CORTEX 框架](../CORTEX.md) 设计你的 agent team。

**先分析认知需求**——你的工作流需要哪些思维动作？

| 函数 | 做什么 | 你的场景中占多大比重？ |
|------|--------|---------------------|
| **Probe** | 探索、发散、发现可能性 | |
| **Judge** | 评估、筛选、做决策 | |
| **Weave** | 整合碎片、构建叙事 | |
| **Anchor** | 执行落地、保持一致 | |

**再映射到角色**——角色 = 认知函数的组合：

| 角色 | 组合 | 职责 |
|------|------|------|
| **Synthesizer** | Probe + Weave | 理解意图，转化为结构化任务 |
| **Implementer** | Anchor + Weave | 生成和执行 |
| **Evaluator** | Judge + Probe | 质量控制、对立视角 |
| **Coordinator** | Weave + Anchor + Judge | 系统状态、冲突解决 |

**从小到大**，不需要一步到位：

| 阶段 | 配置 | 何时适用 |
|------|------|---------|
| Phase 0 | 1 个 agent | 先跑起来，体验价值 |
| Phase 1 | 2 个 agent | 一个想，一个做 |
| Phase 2 | 3-4 个 agent | 加入评估和协调 |
| Phase 3 | 完整团队 | 高复杂度场景 |

#### Step 4 — 创建 Agent 文件（可选）

如果你想让 agent 有持久记忆和身份，创建 agent 目录结构：

```
your-project/
├── AGENTS.md                     # 跨工具协作指南（核心）
├── CLAUDE.md                     # Claude Code 配置（如果你用 Claude Code）
└── .agents/                      # 或 shared/agents/，按项目习惯
    ├── cards/                    # Agent 身份卡 (JSON)
    │   └── <name>.json
    ├── memory/                   # Agent 持久记忆
    │   ├── _template/
    │   │   ├── profile.md
    │   │   └── lessons.md
    │   └── <name>/
    │       ├── profile.md
    │       └── lessons.md
    └── coordination.md           # 协作协议（可选）
```

Agent 身份卡模板可从 Cardo 复制：`cp cardo/templates/agent-card.json .agents/cards/<name>.json`

## CORTEX 框架详解

CORTEX（Cognitive-Operational Role Taxonomy & EXecution）是角色设计的核心方法论。

它回答一个问题：**不管什么场景，如何设计一个恰到好处的 agent team？**

与 Meridian 的关系：Meridian（经络）是协作的骨架和通路，CORTEX（皮层）是每个节点上的智能——合在一起构成完整的数字神经系统。

详细文档见 [CORTEX 框架](../CORTEX.md)，包含：
- 双层架构详解（认知层 + 角色层）
- 可选横切扩展（Memory / Governance / Sensing / Learning）
- 5 个场景的完整映射示例（开发 / 金融 / 内容 / 学术 / 商业）

## 场景适配

CORTEX 不绑定任何特定场景。任何工作流都可以用 Probe/Judge/Weave/Anchor 分析认知需求，再映射到四种协作角色。

详细的场景映射参考见 [CORTEX 框架](../CORTEX.md#场景适配示例)。

## Cardo 命令

Cardo 提供可复制到项目中的 Claude Code slash commands：

| 命令 | 作用 |
|------|------|
| `/cardo-adopt [项目路径]` | 采纳向导 — 分析项目、设计 agent team、生成配置 |

复制方式：`cp cardo/commands/*.md ~/your-project/.claude/commands/`

你也可以在自己的项目中创建自定义命令，放在 `.claude/commands/` 中（仅限 Claude Code）。

## 下一步

1. 先在你的项目中创建 `AGENTS.md`（Phase 0，工具无关）
2. 按你使用的工具添加专属配置（`CLAUDE.md` / `.cursorrules` 等）
3. 需要完整方案时，复制 `cardo-adopt` 命令到项目中运行 `/cardo-adopt`
4. 深入了解角色设计：[CORTEX 框架](../CORTEX.md)
