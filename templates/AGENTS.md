# [项目名] — Multi-Agent Collaboration Guide

> 所有 AI agent 在开始工作前请先读完此文件。
> 本文件基于 [Cardo](https://github.com/pure-maple/cardo) 框架生成。

## 项目简介

（一段话说明项目是什么、用什么技术栈、主要目标）

## Agent Team

| Name | Model | Role | Scope |
|------|-------|------|-------|
| _(register here)_ | | | |

### How to register

1. Add yourself to the table above
2. Create agent card: `.agents/cards/<name>.json`
3. Copy memory template: `cp -r .agents/memory/_template/ .agents/memory/<name>/`

## Task Management

（使用什么任务管理工具？GitHub Issues / Linear / Jira / 本地）

Reference the issue ID in every commit:
`git commit -m "feat: description (ISSUE-xxx)"`

## Task Lifecycle

```
AVAILABLE → CLAIMED → IN_PROGRESS → PR_READY → MERGED → DONE
```

## Key Rules

- Never push directly to `main` — always PR workflow
- Never modify another agent's memory files
- （添加你的项目特有规则）

## CORTEX Role Reference

Agent team 的角色设计基于 CORTEX 框架（Cognitive-Operational Role Taxonomy & EXecution）：

**认知函数**：Probe（探索）/ Judge（评估）/ Weave（整合）/ Anchor（执行）
**协作角色**：Synthesizer / Implementer / Evaluator / Coordinator

详见 [CORTEX 框架文档](https://github.com/pure-maple/cardo/blob/main/CORTEX.md)。
