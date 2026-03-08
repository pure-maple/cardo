# CORTEX Framework

> Cognitive-Operational Role Taxonomy & EXecution
> Cardo 多智能体协作框架的角色分类方法论

## 定位

Cardo（主轴/骨架）定义协作的结构，CORTEX（皮层）定义每个节点上的智能。两者合在一起构成完整的多智能体协作体系——Cardo 是骨架，CORTEX 是大脑。

命名意象上，CORTEX 与 Meridian（灵枢/经络）形成神经系统隐喻：经络负责传导，皮层负责思考。

CORTEX 回答一个核心问题：**不管什么场景，如何设计一个恰到好处的 agent team？**

## 双层架构

CORTEX 由两层正交组成，不应混淆或合并：

### 认知函数层（How we think）

任何复杂任务都需要经历的四类思维动作：

| 函数 | 职责 | 关键动作 |
|------|------|---------|
| **Probe** | 探索、发散、生成可能性 | 搜索、提问、假设、头脑风暴 |
| **Judge** | 评估、筛选、做决策 | 验证、批判、风险分析、证伪 |
| **Weave** | 整合碎片、构建叙事 | 串联、架构、框架设计、意义生成 |
| **Anchor** | 执行落地、保持一致 | 编码、写作、计算、格式化、交付 |

### 协作角色层（How we work）

团队中真正承担责任、交付和握手的角色：

| 角色 | 职责 | 认知函数组合 |
|------|------|------------|
| **Synthesizer** | 理解模糊意图，转化为结构化任务 | Probe + Weave |
| **Implementer** | 承担生成和执行工作 | Anchor + 局部 Weave |
| **Evaluator** | 质量控制、逻辑校验、对立视角 | Judge + 对抗式 Probe |
| **Coordinator** | 维护系统状态，解决冲突，交付组合 | 系统级 Weave + Anchor + 少量 Judge |

### 核心洞察

角色不等于函数。角色 = 认知函数的特定组合 + 交付责任。

同一个认知函数可以出现在不同角色中：Probe 既出现在 Synthesizer（探索需求）中，也出现在 Evaluator（主动找漏洞）中。区别在于目的和责任归属。

## 可选扩展（横切关注点）

核心四角色之外，根据场景需要可挂载的横切能力：

| 扩展 | 作用 | 何时启用 |
|------|------|---------|
| **Memory** | 长期记忆、知识沉淀、跨项目经验 | 团队持续运行、需要跨会话记忆时 |
| **Governance** | 权限、合规、审批、安全边界 | 金融、医疗、法律等受监管领域 |
| **Sensing** | 数据采集、监控、环境感知 | 实时系统、爬虫、监控场景 |
| **Learning** | 复盘、调优、自我改进 | 团队演化阶段、需要持续优化时 |

横切扩展不是独立角色，而是附加在角色上的能力模块。例如 Coordinator + Memory = 有长期记忆的编排者。

## 演化阶段

用户不需要一步到位。CORTEX 支持从最小配置渐进演化：

| 阶段 | 配置 | 适用场景 | 示例 |
|------|------|---------|------|
| **Phase 0** | 1 个通用 agent | 单人增强，先跑起来 | 一个 Anchor 帮你写代码/写文档 |
| **Phase 1** | 2 个 agent | 双人搭档，一个想一个做 | Synthesizer + Implementer |
| **Phase 2** | 3-4 个 agent | 补齐评估和协调 | 加入 Evaluator 或 Coordinator |
| **Phase 3** | 完整团队 + 扩展 | 生态演化，挂载横切能力 | 全角色 + Memory + Governance |

每个 Phase 都是独立可交付的。Phase 0 就能产生价值。

## 场景适配示例

CORTEX 不绑定任何特定场景。以下是不同领域的角色映射参考：

### 软件开发

| 角色 | Agent 职责 | 主要认知函数 |
|------|-----------|------------|
| Synthesizer | 需求分析、PRD、架构设计 | Probe（探索技术方案）+ Weave（整合架构） |
| Implementer | 编码、测试、部署 | Anchor（执行）+ Weave（局部整合） |
| Evaluator | Code review、安全审计、性能测试 | Judge（评估质量）+ Probe（找漏洞） |
| Coordinator | 版本管理、发版、冲突解决 | Weave（集成）+ Anchor（发版流程） |

### 金融投资研究

| 角色 | Agent 职责 | 主要认知函数 |
|------|-----------|------------|
| Synthesizer | 信息搜集、行业扫描、投资叙事构建 | Probe（找标的）+ Weave（构建 thesis） |
| Implementer | 财务建模、数据可视化、跟踪表 | Anchor（模型计算）+ Weave（报告整合） |
| Evaluator | 风险评估、压力测试、证伪 | Judge（偏差校正）+ Probe（反面论证） |
| Coordinator | 组合管理、仓位平衡、复盘节奏 | Weave（多策略整合）+ Judge（冲突裁决） |

### 内容创作

| 角色 | Agent 职责 | 主要认知函数 |
|------|-----------|------------|
| Synthesizer | 选题策划、受众分析、角度设计 | Probe（热点发现）+ Weave（叙事框架） |
| Implementer | 写作、剪辑、素材制作 | Anchor（出稿）+ Weave（内容结构） |
| Evaluator | 事实核查、调性审校、数据复盘 | Judge（质量评估）+ Probe（合规检查） |
| Coordinator | 排期管理、多平台适配、品牌一致性 | Weave（跨平台整合）+ Anchor（分发执行） |

### 学术研究

| 角色 | Agent 职责 | 主要认知函数 |
|------|-----------|------------|
| Synthesizer | 文献综述、研究问题塑形 | Probe（领域扫描）+ Weave（理论框架） |
| Implementer | 实验设计、数据分析、论文撰写 | Anchor（实验执行）+ Weave（章节逻辑） |
| Evaluator | 模拟审稿、方法论批判、统计检验 | Judge（Reviewer 视角）+ Probe（找方法漏洞） |
| Coordinator | 版本管理、引用一致性、投稿策略 | Weave（全文一致性）+ Judge（期刊匹配） |

### 商业计划

| 角色 | Agent 职责 | 主要认知函数 |
|------|-----------|------------|
| Synthesizer | 市场调研、竞品分析、价值主张 | Probe（机会发现）+ Weave（商业叙事） |
| Implementer | 财务模型、路线图、融资材料 | Anchor（模型搭建）+ Weave（材料整合） |
| Evaluator | 投资人视角挑战、风险评估 | Judge（商业模式证伪）+ Probe（找致命假设） |
| Coordinator | BP 整体故事线、路演节奏 | Weave（愿景与执行的张力管理） |

## 设计原则

1. **认知先于角色**：先用 Probe/Judge/Weave/Anchor 检查任务需要哪些思维动作，再决定由谁承担
2. **角色 = 函数组合 + 交付责任**：不要把认知函数当角色用，角色必须有明确的交付物和责任边界
3. **最小必要**：从 Phase 0 开始，按需演化，不过度设计
4. **场景驱动**：先理解工作方式，再推荐角色配置，不套模板
5. **横切按需**：Memory/Governance/Sensing/Learning 只在真正需要时挂载

## 命名决策

### 选定：CORTEX

**全称**：Cognitive-Operational Role Taxonomy & EXecution

**选择理由**：
1. **神经系统隐喻**——Cortex（皮层）是认知加工与决策的中枢。与 Cardo（骨架/主轴）和 Meridian（经络/通路）共同构成完整的数字神经系统。
2. **语义精准**——Cortex 是大脑处理高级认知、决策和整合的部位，完美对应"认知函数层 + 角色层"的双层架构。
3. **API 友好**——`cortex.functions.probe`、`cortex.roles.synthesizer`、`cortex.extensions.memory`，命名空间自然。
4. **发音有力**——/ˈkɔːrteks/，技术权威感强，国际通用。

**决策过程**：4 模型讨论（Codex/Gemini/Kimi/Qwen），Gemini 提出 CORTEX，Maple 批准（2026-03-08）。

### 备选

| 名称 | 全称 | 备注 |
|------|------|------|
| **PRAXIS** | Probative Role Architecture for eXecutive Intelligent Systems | 希腊语"实践智慧"（πραξις），理论与实践的统一。零商标冲突，哲学深度强。与灵枢"辨证施治"的中医哲学同源。Kimi 推荐，评分 20/20。适合学术发表或需要更强品牌独占性时替换使用。 |
| **CORA** | Cognitive-Operational Role Architecture | Codex 提出。双层结构描述最准确，但品牌空间拥挤（多个同名产品）。 |
| **MARC** | Meta-Agent Role Classification | 学术感强，但"Classification"偏静态，与动态组合设计理念有张力。 |

### 淘汰

| 名称 | 淘汰理由 |
|------|---------|
| **Cognex** | 纳斯达克上市公司（CGNX），机器视觉巨头，商标风险极高 |

## 来源

本框架由 [Meridian](https://github.com/pure-maple/Meridian) agent team 通过多轮多模型讨论协作设计：
- 认知函数层（Probe/Judge/Weave/Anchor）：Kimi 提出，团队共识
- 协作角色层（Synthesizer/Implementer/Evaluator/Coordinator）：Gemini 提出，团队共识
- 双层融合架构：Codex 提出"角色 = 函数组合"的关键洞察
- 演化阶段论：Kimi 提出，团队采纳
- 横切扩展：Codex 提出四项核心扩展，Kimi 补充 Empath/Taste
- CORTEX 命名：Gemini 提出，4 模型讨论，Maple 批准（2026-03-08）
- 场景验证：5 场景（开发/金融/内容/学术/商业）全部通过 3 模型独立验证
