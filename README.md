# Cardo

> 多智能体协作框架——帮你在任何项目中从零建立 agent team

**Cardo**（拉丁语：铰链 / 轴 / 城市主轴）来自罗马城市规划中的南北主轴 *cardo maximus*，一切街区围绕它展开。Cardo 是多智能体协作的骨架——定义角色、规范协作、引导采纳。

## 这是什么

Cardo 提供一套工具无关、场景通用的多智能体协作框架：

- **CORTEX 角色分类法** — 认知函数（Probe/Judge/Weave/Anchor）与协作角色（Synthesizer/Implementer/Evaluator/Coordinator）的双层架构
- **Cairn 采纳向导** — 交互式引导用户分析项目、设计 agent team、生成配置
- **项目模板** — AGENTS.md、agent 身份卡、协作协议等开箱即用的模板
- **Cardo 命令** — 可复制到项目中的 slash command 模板

## 不绑定特定工具

Cardo 不假设你用什么 AI 工具。Claude Code、Codex、Gemini CLI、Cursor、Windsurf——都可以。`AGENTS.md` 是跨工具通用的协作指南，工具专属配置按需添加。

## 快速开始

### 1. 复制模板到你的项目

```bash
# 复制 AGENTS.md 模板
cp cardo/templates/AGENTS.md ~/your-project/AGENTS.md

# 如果需要 agent 持久记忆
mkdir -p ~/your-project/.agents/{cards,memory}
cp cardo/templates/agent-card.json ~/your-project/.agents/cards/_template.json
cp -r cardo/templates/memory-template/ ~/your-project/.agents/memory/_template/
```

### 2. 用 Cairn 自动引导（需要 Claude Code）

```bash
# cardo-adopt 命令需要先复制到你的 .claude/commands/ 中
cp cardo/commands/cardo-adopt.md ~/your-project/.claude/commands/

# 然后在项目目录下的 Claude Code 中运行
/cardo-adopt
```

### 3. 了解 CORTEX 框架

读 [CORTEX.md](CORTEX.md) 理解角色设计方法论，然后按你的场景设计 agent team。

## 目录结构

```
cardo/
├── CORTEX.md              # CORTEX 角色分类框架
├── agents/
│   └── cairn/             # 内置采纳向导 agent
│       ├── card.json
│       └── profile.md
├── templates/             # 用户项目模板
│   ├── AGENTS.md
│   ├── agent-card.json
│   ├── coordination.md
│   └── memory-template/
│       ├── profile.md
│       └── lessons.md
├── commands/              # Cardo 命令模板
│   └── cardo-adopt.md
└── docs/
    └── adoption-guide.md  # 详细采纳指南
```

## 与 Meridian 的关系

Cardo 是 [Meridian](https://github.com/pure-maple/Meridian)（灵枢）的子模块之一。Meridian 是个人 AI 智能体协作中枢，Cardo 是其中可独立使用的协作框架层。

| 模块 | 定位 |
|------|------|
| **Cardo** | 协作框架（角色分类、采纳引导、模板） |
| **modelmux** | 模型编排引擎（智能路由、多模型协作） |
| Meridian | 私有 umbrella（个人工作流、agent 记忆） |

你不需要 Meridian 或 modelmux 就能使用 Cardo。
