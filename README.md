# Awesome Harness Engineering 中文说明

> 一个面向 **Harness Engineering（AI Agent 运行编排工程）** 的高质量资料仓，聚焦如何让 Agent 在真实任务中更稳定、更可控、更可验收，而不是只会在单轮对话里“看起来很聪明”。

---

## 1. 这是什么

`awesome-harness-engineering` 不是一个泛 AI 链接收藏夹，也不是普通的“Agent 工具大全”。

它关注的是一个更窄、但真正决定 Agent 能否落地的问题：

> **如何给 AI Agent 搭建一套可靠的运行环境（Harness），让它在真实项目里能持续工作，而不是做几轮对话就漂。**

这里收录的内容主要包括：
- 方法论文章
- 上下文工程实践
- 约束与安全控制
- AGENTS / Spec / Workflow 设计规范
- Evals 与 Observability
- Benchmarks
- 运行时 / Harness / 开源实现

你可以把它理解成：

> **研究“怎么把 AI 从会聊天，变成能交付”的资料地图。**

---

## 2. 什么是 Harness Engineering

很多人讨论 AI Agent 时，重点都放在：
- 模型强不强
- Prompt 写得好不好
- 工具调得顺不顺

但真正把 Agent 用进项目后，很快会撞到一堆更现实的问题：
- 上下文太长，任务做一半忘了前文；
- 多步骤任务中途漂移，越做越偏；
- 同样一个任务，这次能成，下次就翻车；
- 看起来执行了很多步骤，但没有真实验收；
- 失败之后没有 trace、没有分类、没有回放依据；
- 多 agent 协作时，职责不清、交接混乱；
- 脚本、配置、权限、环境这些“非模型问题”，反而成了真实瓶颈。

Harness Engineering 处理的就是这些问题。

它不是在问：
- “模型还能不能再强一点？”

而是在问：
- “即便模型能力有波动，系统怎么设计才能稳定交付？”

所以它更接近软件工程，而不是提示词技巧。

---

## 3. 这个仓库的价值在哪里

这个仓库最有价值的地方，不是它“收了很多链接”。

真正值钱的是它把 harness engineering 拆成了几层清晰的问题域：
- Foundations
- Context / Memory / Working State
- Constraints / Guardrails / Safe Autonomy
- Specs / Agent Files / Workflow Design
- Evals / Observability
- Benchmarks
- Runtimes / Harnesses / Reference Implementations

这意味着它不是杂乱堆资料，而是在构建一张问题地图：

- 你如果想解决“上下文漂移”，该去看哪一类内容；
- 你如果想解决“任务验收不稳定”，该看哪一类内容；
- 你如果想搭建自己的 runtime / harness，该看哪类开源实现；
- 你如果想做 benchmark 对照实验，该从哪几套基线开始。

这类结构化资料仓，很适合作为：
- 团队研究入口；
- 方法论归档入口；
- 模板和标准抽取入口；
- 后续工程资产沉淀的上游输入层。

---

## 4. 当前内容分区怎么理解

### 4.1 Foundations

这一部分主要回答：
- Harness engineering 是什么；
- 它和 context engineering、agent runtime、agent ops 的关系是什么；
- 为什么很多 Agent 失败，其实不是模型问题，而是 harness 问题。

适合：
- 第一次接触这个概念；
- 需要统一团队认知；
- 需要给别人解释“为什么不能只靠 prompt”。

### 4.2 Context, Memory & Working State

这一部分主要讨论：
- 如何管理上下文窗口；
- 如何保留长期任务状态；
- 如何把失败经验、文件系统状态、工作记忆组织好；
- 如何减少上下文污染和无效 token 消耗。

这部分特别关键，因为很多 agent 在长任务里失控，本质都是上下文管理失败。

### 4.3 Constraints, Guardrails & Safe Autonomy

这一部分重点是：
- 权限控制
- 工具边界
- 自动化执行时的安全收口
- 如何减少人工审批但不丢控制力

适合：
- 正在做生产环境 agent；
- 要求可审计、可限制、可回滚；
- 需要设计“能自动执行，但不能乱执行”的系统。

### 4.4 Specs, Agent Files & Workflow Design

这一部分关注：
- AGENTS.md / agent.md 这类仓库级说明文件；
- Spec 驱动开发；
- 工作流与任务结构设计；
- 如何让 agent 不是“想到哪做到哪”，而是沿着明确结构工作。

这是最容易直接转成团队工程规范的一层。

### 4.5 Evals & Observability

这一部分是把“我觉得它做得不错”变成“它真的做得不错”的关键。

它解决的是：
- 怎么定义成功；
- 怎么看 trace；
- 怎么做任务级评测；
- 怎么发现 regressions；
- 怎么区分偶然成功和稳定成功。

如果没有这层，任何 Agent 项目都会停留在“演示还不错”的阶段。

### 4.6 Benchmarks

这一部分收录了大量与 Agent 可靠性相关的 benchmark。

重点不是为了追榜，而是为了：
- 做对照实验；
- 看不同 harness 结构的差异；
- 找到更接近真实任务的验证环境；
- 建立自己的基线。

### 4.7 Runtimes, Harnesses & Reference Implementations

这一部分更偏实现层，回答的是：
- 别人是怎么搭 runtime 的；
- session、tool、workflow、agent orchestration 怎么组织；
- 有哪些开源项目值得拆解学习。

适合：
- 打算自己做运行时；
- 想看成熟参考实现；
- 想把理念真正变成系统。

---

## 5. 这个仓库不做什么

为了避免误解，这里要说清楚边界。

这个仓库**不追求**：
- 泛 AI 工具导航
- 纯模型资讯汇总
- 新闻式热点跟踪
- 大而全的 agent framework 对比网站
- “什么都收一点”的资源站

只有当一篇内容和下面这些问题直接相关时，才应该收：
- harness 设计
- context 管理
- task state / workflow state
- 运行控制
- eval / observability
- safe autonomy
- runtime / orchestration
- 长任务可靠性

这个边界非常重要。

因为一旦边界松掉，仓库很快会退化成普通 AI 收藏夹，失去现在最值钱的“问题聚焦度”。

---

## 6. 谁适合看这个仓库

这个仓库最适合下面几类人：

### 6.1 正在做 Coding Agent / Research Agent 的人
如果你已经在真实项目里用 Agent，而不是只在聊天窗口里试试玩，这个仓库会很有价值。

### 6.2 正在搭建 Agent 平台 / Agent Runtime 的人
你需要的不是“再换一个模型”，而是：
- session 怎么保存
- context 怎么组织
- tools 怎么约束
- eval 怎么做
- workflow 怎么设计

### 6.3 想把 AI 工作流工程化的团队
当团队规模变大后，prompt 已经不够了，真正需要的是：
- 标准化
- 模板化
- 可观测
- 可交接
- 可回归

### 6.4 想把 TCD 往上游研究和下游工程打通的人
如果你不是在做纯研究，而是想把外部高价值方法论转成自己团队的资产，这个仓库特别合适做上游输入层。

---

## 7. 如何使用这个仓库

建议不要“从头到尾顺序看”。

更好的用法是按问题进入。

### 场景 1：你现在的 Agent 经常忘事、做长任务漂移
优先看：
- Context / Memory & Working State
- Foundations

### 场景 2：你已经能跑，但总感觉结果不稳定
优先看：
- Evals & Observability
- Constraints / Guardrails & Safe Autonomy

### 场景 3：你想给团队建立统一 Agent 项目规范
优先看：
- Specs / Agent Files & Workflow Design
- Foundations

### 场景 4：你想做自己的 runtime / workflow 系统
优先看：
- Runtimes, Harnesses & Reference Implementations
- Specs / Workflow Design
- Evals

### 场景 5：你想建立可对照、可复现的实验基线
优先看：
- Benchmarks
- Evals & Observability

---

## 8. 它和 TCD 的关系

这个仓库和 TCD 的关系，不应该是“平行存在”，而应该是上下游关系。

### 8.1 这个仓库负责输入
它负责：
- 聚合高质量外部文章；
- 追踪 harness engineering 的关键问题域；
- 维护一张研究地图；
- 帮我们快速找到值得吸收的方法论。

### 8.2 TCD 负责转译和落地
TCD 负责把这些内容转成：
- 模板
- 标准
- 工作流
- 验收规则
- benchmark adapter
- 编排系统

也就是说：

> 这个仓库回答“别人怎么做”，TCD 回答“我们怎么落地成自己的系统”。

### 8.3 已有的融合方案文档
如果你关心的不是“这仓库是什么”，而是：
- 哪些东西应该融合进 TCD；
- 哪些方向最值得做成自己的资产；
- 落地顺序应该怎么排；

请直接看：

- [TCD × Harness Engineering 深度融合方案](./TCD_FUSION_PLAN.md)

---

## 9. 推荐的阅读顺序

如果你第一次进入这个仓库，建议按下面顺序看：

### 路线 A：理解概念
1. Foundations
2. Context / Memory
3. Guardrails

### 路线 B：面向工程落地
1. Specs / Agent Files / Workflow Design
2. Evals & Observability
3. Runtimes / Harnesses

### 路线 C：面向实验和对照
1. Evals & Observability
2. Benchmarks
3. Runtimes / Reference Implementations

### 路线 D：面向 TCD 融合
1. 先看本文件
2. 再看 `README.md`
3. 再看 `TCD_FUSION_PLAN.md`

---

## 10. 后续建议怎么扩展

如果这个仓库后续要继续演进，建议不是只加链接，而是逐步增加下面几类内容：

### 10.1 中文导读层
不是翻译所有文章，而是做高质量中文导读和提炼，让团队快速判断哪些值得深读。

### 10.2 模板抽取层
把文章和案例中的高价值结构，抽成：
- AGENTS 模板
- init/check 模板
- handoff 模板
- eval schema 模板

### 10.3 标准化层
沉淀成：
- TCD Agent Standard Kit
- 统一字段结构
- 统一 workflow 节点语义
- 统一验收出口

### 10.4 benchmark adapter 层
把 benchmark 从“收录链接”升级成“可接、可跑、可对照”。

---

## 11. 最终定位

这个仓库最合理的定位不是：

> “一个 AI Agent 资料收藏夹”

而是：

> **一个面向 TCD 与工程落地的 Harness Engineering 研究地图。**

它的使命不是“告诉你世界上有哪些链接”，而是：
- 帮你快速找到高信号方法论；
- 帮你理解 Agent 稳定性的关键问题；
- 为 TCD 和后续系统建设提供上游知识输入；
- 为模板、标准、工作流、验收层、实验层提供研究来源。

如果后面继续按这个方向推进，它就会从一个资料仓，变成一个真正有战略价值的上游研究入口。

---

## 12. 相关文档

- 英文主文档：[README.md](./README.md)
- TCD 融合方案：[TCD_FUSION_PLAN.md](./TCD_FUSION_PLAN.md)



---

## 英文版文档

- [README.en.md](./README.en.md)
- [TCD × Harness Engineering 深度融合方案](./TCD_FUSION_PLAN.md)
