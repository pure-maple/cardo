# Cardo

> 多智能体协作框架——帮你在任何项目中从零建立 agent team

**Cardo**（拉丁语：铰链 / 轴 / 城市主轴）来自罗马城市规划中的南北主轴 *cardo maximus*。城市的一切街区围绕它展开——Cardo 框架也是如此：定义角色、规范协作、引导采纳，成为你多智能体协作的骨架。

## Cardo 是什么

一套**工具无关、场景通用**的多智能体协作框架。它解决一个问题：

> 当你想让多个 AI agent 协同工作时，如何设计角色、规范协作、渐进演化？

| 组件 | 作用 |
|------|------|
| [**CORTEX**](CORTEX.md) | 角色设计方法论——认知函数（Probe/Judge/Weave/Anchor）× 协作角色（Synthesizer/Implementer/Evaluator/Coordinator）的双层架构 |
| **Cairn** | 采纳向导——交互式分析项目、检测现有 AI 框架、设计 agent team、生成配置 |
| **模板** | AGENTS.md、agent 身份卡、协作协议等开箱即用的项目模板 |
| **命令** | 可复制到项目中的 slash command（如 `/cardo-adopt`） |

### Cardo 不是什么

- **不是个人工作流**——那是你自己的项目
- **不是模型编排引擎**——那是 [modelmux](https://github.com/pure-maple/modelmux)（可选增强）
- **不绑定特定 AI 工具**——Claude Code、Codex、Gemini CLI、Cursor、Windsurf 都可以

## 用户旅程

```
Phase 0 ─── 复制 AGENTS.md 模板，1 个 agent 先跑起来
  │
Phase 1 ─── 用 CORTEX 分析认知需求，设计 2 个互补角色
  │
Phase 2 ─── 运行 /cardo-adopt 让 Cairn 全面引导，3-4 个 agent 协作
  │
Phase 3 ─── 引入 modelmux 智能路由，完整团队 + 横切扩展
  │
 进阶  ─── 构建你自己的 umbrella（私有配置 + 公开框架的分层模式）
```

每个阶段独立可交付。Phase 0 就能产生价值——不需要一步到位。

## 快速开始

### 最快的方式：复制模板

```bash
# 克隆 Cardo
git clone https://github.com/pure-maple/cardo.git

# 复制 AGENTS.md 到你的项目
cp cardo/templates/AGENTS.md ~/your-project/AGENTS.md

# 按需添加 agent 持久记忆
mkdir -p ~/your-project/.agents/{cards,memory}
cp cardo/templates/agent-card.json ~/your-project/.agents/cards/_template.json
cp -r cardo/templates/memory-template/ ~/your-project/.agents/memory/_template/
```

### 完整引导：Cairn 采纳向导（需要 Claude Code）

```bash
# 复制采纳命令到你的项目
mkdir -p ~/your-project/.claude/commands
cp cardo/commands/cardo-adopt.md ~/your-project/.claude/commands/

# 在项目目录下的 Claude Code 中运行
/cardo-adopt
```

Cairn 会：扫描项目现状 → 检测现有 AI 框架 → 交互式讨论需求 → 设计 agent team → 生成全套配置。

### 深入理解：CORTEX 角色设计

读 [CORTEX.md](CORTEX.md) 理解角色分类方法论，然后按你的场景设计 agent team。CORTEX 不绑定特定场景——开发、金融、内容创作、学术研究、商业计划，都有对应的角色映射。

## 架构

```
┌─────────────────────────────────────────────────┐
│                   你的项目                        │
│                                                 │
│  AGENTS.md          .agents/cards/<name>.json   │
│  CLAUDE.md (可选)    .agents/memory/<name>/      │
│  .cursor/ (可选)     coordination.md (可选)       │
│                                                 │
│  ← Cardo 模板生成 / Cairn 交互式引导产出          │
└───────────────┬─────────────────┬───────────────┘
                │ 采纳             │ 可选增强
                ▼                  ▼
┌───────────────────┐   ┌───────────────────┐
│      Cardo        │   │     modelmux      │
│                   │   │                   │
│ CORTEX 角色分类    │   │ 智能路由           │
│ Cairn 采纳向导     │   │ 多模型协作         │
│ 项目模板           │   │ 成本优化           │
│ 命令模板           │   │ 上下文压缩         │
└───────────────────┘   └───────────────────┘
    协作框架                 模型编排引擎
```

**Cardo 回答**：如何组织你的 agent team？（角色设计、协作规范、渐进演化）

**modelmux 回答**：如何把任务路由到合适的模型？（智能路由、多模型协作、成本优化）

两者独立可用，组合使用效果更强。

## 工具无关

`AGENTS.md` 是跨工具通用的协作指南。任何 AI CLI 都会读取它。工具专属配置按需添加：

| AI 工具 | 配置文件 | 说明 |
|---------|---------|------|
| Claude Code | `CLAUDE.md` | 角色体系、索引、硬约束 |
| Codex | `AGENTS.md`（已有） | Codex 原生支持 AGENTS.md |
| Cursor | `.cursor/rules/` | Cursor rules |
| Windsurf | `.windsurfrules` | Windsurf 配置 |
| Gemini CLI | `GEMINI.md` 或 `AGENTS.md` | Gemini 配置 |

同时使用多个工具时，`AGENTS.md` 是唯一的跨工具共享层。

## 进阶：构建你的 umbrella

当多智能体实践成熟后，你可能会希望建立自己的"总部"——一个私有的 umbrella 仓库：

```
your-hub/                   # 你的私有仓库
├── shared/                 # agent 记忆、工作流配置
│   ├── agents/memory/      # 持久记忆（个性化，不开源）
│   └── ops/                # 运维、交接、自动化
├── cardo/                  # 公开子模块：协作框架
├── modelmux/               # 公开子模块：模型编排
├── your-private-tools/     # 你的私有工具
├── AGENTS.md               # 你的团队协作规范
└── CLAUDE.md               # 你的 Claude Code 配置
```

**关键原则**：个性化配置留在你的仓库里，不污染公开子模块。

这是 [Meridian](https://github.com/pure-maple/Meridian)（灵枢）采用的模式——Meridian 是 Cardo 框架的第一个 umbrella 实例，也是 Cardo 的诞生地。

## 目录结构

```
cardo/
├── CORTEX.md              # 角色分类框架（核心方法论）
├── agents/
│   └── cairn/             # 内置采纳向导 agent
│       ├── card.json
│       └── profile.md
├── templates/             # 用户项目模板
│   ├── AGENTS.md
│   ├── agent-card.json
│   ├── coordination.md
│   └── memory-template/
├── commands/              # 命令模板（Claude Code slash commands）
│   └── cardo-adopt.md
└── docs/
    └── adoption-guide.md  # 详细采纳指南
```

## 设计哲学

- **诊断先于处方** — 先理解项目现状，再给建议
- **最小可行** — Phase 0 就能产生价值，不追求一步到位
- **工具无关** — 不假设用户用什么 AI 工具
- **场景通用** — CORTEX 适用于任何需要多智能体协作的领域
- **整合优于堆叠** — 有价值的迁移过来，冗余的清理掉

## 了解更多

| 主题 | 文档 |
|------|------|
| 角色设计方法论 | [CORTEX.md](CORTEX.md) |
| 详细采纳指南 | [docs/adoption-guide.md](docs/adoption-guide.md) |
| 模型编排增强 | [modelmux](https://github.com/pure-maple/modelmux) |

## 来源

Cardo 从 [Meridian](https://github.com/pure-maple/Meridian)（灵枢——个人 AI 智能体协作中枢）中抽离而来，是其中可独立使用的协作框架层。CORTEX 框架和 Cairn 采纳向导均由 Meridian agent team 通过多模型协作设计。
