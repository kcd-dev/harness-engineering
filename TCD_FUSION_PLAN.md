# TCD × Harness Engineering 深度融合方案

## 一、文档目的

这份文档不是在讨论“要不要 fork 一个 awesome list”，而是在明确一件更现实的事：

> **如何把 `awesome-harness-engineering` 这个上游研究仓，升级成 TCD 体系里的可执行工程资产入口。**

当前仓库已经完成了一件事：
- 它把 harness engineering 相关资料按主题做了高质量聚合；
- 它覆盖了 foundations、context、guardrails、specs、evals、benchmarks、runtimes 等关键层；
- 它适合作为研究入口、资料导航和趋势观察面板。

但它还没有完成更值钱的部分：
- 还没有把这些资料沉淀成 TCD 可复用模板；
- 还没有把 eval / trace / benchmark 转成 TCD 的统一验收层；
- 还没有形成我们自己的项目脚手架、工作流编排器和对照实验基线；
- 还没有从“资料仓”升级成“产能仓”。

所以这份方案文档的目标很明确：

1. 判断这个仓库里哪些内容值得吸收到 TCD；
2. 明确哪些内容适合做成自己的工程资产；
3. 规划一条从“awesome list”走向“可执行系统”的最短路径；
4. 避免陷入“收集很多链接，但没有形成真正产出”的伪繁荣。

---

## 二、先讲结论

### 结论 1：这个仓库最值钱的不是链接本身，而是“结构”

真正可复用的价值不在于：
- 又多收了一篇 Anthropic 文章；
- 又多收了一个 benchmark；
- 又多收了一个 runtime 项目。

而在于：
- 这些资料已经被组织成了 **harness engineering 的问题地图**；
- 这个问题地图可以被 TCD 拆成模板、标准、工作流、验收层、实验基线；
- 这些拆出来的东西，才是后续能持续复用、沉淀、售卖、复制到其他项目的资产。

### 结论 2：不要把这个仓库做成“中文翻译版 awesome list”

那种做法没有壁垒。

因为别人也能抄，搜索引擎也能做，AI 也能几秒钟总结。

如果只是继续补链接、补摘要、补标签，最后只会得到：
- 信息量看起来很大；
- 但无法直接交付；
- 无法直接指导执行；
- 无法直接缩短项目周期；
- 无法形成 TCD 的独有优势。

### 结论 3：最应该做的是“五层转译”

把仓库里的资料按下面五层转成 TCD 资产：

1. **模板层**：把文章知识转成可执行模板；
2. **标准层**：把 specs / agents / guide 转成组织标准；
3. **编排层**：把 runtime / harness 变成工作流系统；
4. **验收层**：把 eval / observability 变成统一验收机制；
5. **实验层**：把 benchmark 变成对照实验和基线证明系统。

这五层一旦打通，这个仓库就不再是阅读仓，而会变成：

> **TCD 的上游研究输入口 + 下游工程资产生成器。**

---

## 三、为什么它适合和 TCD 融合

### 3.1 两者关注的问题是同一类问题

`awesome-harness-engineering` 讨论的是：
- 如何给 AI Agent 提供稳定上下文；
- 如何约束 Agent 行为；
- 如何让多步任务不中途漂移；
- 如何做 eval、trace、observability；
- 如何让 agent runtime 更可靠。

TCD 讨论的是：
- 如何让 AI 不再靠记忆执行，而是靠脚本执行；
- 如何把流程固化成程序和配置；
- 如何降低多轮任务中的遗忘、漂移和人工干预；
- 如何让项目可初始化、可中断、可恢复、可验收。

本质上，它们都在解决同一个问题：

> **如何把“AI 很聪明但不稳定”变成“系统可执行且可控”。**

### 3.2 awesome 仓解决的是“研究面”，TCD 更擅长“落地面”

这个仓库的优势：
- 对外部最佳实践的覆盖广；
- 对 harness engineering 的概念分层清晰；
- 能快速告诉我们“这个领域别人都在怎么做”。

TCD 的优势：
- 擅长把原则翻译成模板、命令、脚手架、工作流；
- 擅长把“概念”变成“可执行路径”；
- 擅长把一次次试错收敛成固定机制。

所以最优关系不是二选一，而是：

- `awesome-harness-engineering` 做 **输入**；
- TCD 做 **转译和落地**；
- 最终形成自己的执行系统。

### 3.3 它正好补足了 TCD 当前的外部理论来源

TCD 现在已经有：
- 模板化思路；
- AI 做翻译、程序做执行的核心原则；
- FCD / workflow / init / check 之类的结构；
- 一些工具化方向（workflow studio、FCD 命令、小白工具集等）。

但 TCD 还缺：
- 一个系统化、外部可引用的 harness engineering 研究底座；
- 一个持续更新的上游资料池；
- 一个对外可解释“我们不是闭门造车”的证据层。

这正是这个仓库的价值。

---

## 四、融合原则

在真正开始做之前，先把原则讲清楚，不然后面很容易做歪。

### 原则 1：不做“资料收集型产品”

我们不把这件事定义成：
- 收集链接；
- 翻译文章；
- 做个导航页；
- 做个排行榜页。

因为这类东西很难形成真正壁垒。

### 原则 2：只吸收能转成执行资产的部分

判断标准很简单：

> **这条资料，能不能在 TCD 里转成模板、标准、工作流、验收规则、实验基线？**

如果能，就吸收。
如果不能，就保留为参考链接，不做产品主干。

### 原则 3：先做最短闭环，不做大而全平台

不要上来就说：
- 做一个 Agent OS；
- 做一个全栈编排平台；
- 做一个 benchmark 云；
- 做一个企业级知识图谱。

这都是典型的过度设计。

正确做法是先打出最短闭环：

- 用资料 → 产出模板；
- 用模板 → 跑真实任务；
- 用真实任务 → 输出验收结果；
- 用验收结果 → 形成复盘与迭代。

### 原则 4：以 TCD 主线为中心，不被外部框架带偏

仓库里会出现很多框架、runtime、标准、benchmark、平台。

要保持清醒：
- 我们不是去做 LangChain 的镜像；
- 不是做 Anthropic 的文档搬运；
- 不是做 OpenAI eval 平台的复制品；
- 不是做 benchmark 资讯号。

我们要做的是：

> **把这些东西中真正有用、可执行、可收敛的部分，吸收到 TCD 体系。**

---

## 五、最值得融合的五个方向（按优先级排序）

---

## 方向一：把资料仓升级成 TCD 模板资产库（最高优先级）

### 5.1 这是什么

把 README 中的高价值知识，不停留在“知道有这么个理念”，而是翻译成真正可以复制到新项目里的模板。

模板类型包括但不限于：
- `init.sh`：项目初始化与环境预检；
- `feature_list.json`：功能清单与范围边界；
- `workflow.json`：任务状态和中断恢复；
- `check.sh`：执行前后的健康检查；
- `handoff.md`：长任务交接文档；
- `validation.md`：验收清单；
- `ops.md`：运行与回滚说明；
- `agents/` 与 `commands/` 目录骨架。

### 5.2 为什么这是最高优先级

因为模板是最短、最直接、最容易产生复利的资产。

对团队来说，模板带来的收益是立即可见的：
- 开新项目更快；
- 初始化更稳定；
- 任务交接更顺；
- 新人接手更容易；
- 经验复用更自然。

相比之下，单纯做研究总结虽然“看起来很深”，但短期很难带来实际产能提升。

### 5.3 可以从这个仓里吸收什么

优先吸收以下主题：
- Context / Memory：转成上下文组织模板；
- Guardrails / Safe Autonomy：转成权限、确认、失败回滚模板；
- Specs / Agent Files：转成仓库标准文件模板；
- Effective harnesses：转成 initializer / handoff / self-check 模板。

### 5.4 最短落地形态

在仓库里新增一个目录，例如：

```text
assets/
  templates/
    coding-agent-project/
    research-agent-project/
    browser-agent-project/
    eval-first-agent-project/
```

每个模板都至少包含：
- `README.md`
- `AGENTS.md`
- `init.sh`
- `feature_list.json`
- `workflow.json`
- `check.sh`
- `handoff-template.md`
- `acceptance-template.md`

### 5.5 形成我们自己的方式

关键不是把别人文章里的段落摘过来，而是形成：
- 我们自己的目录结构；
- 我们自己的字段定义；
- 我们自己的初始化顺序；
- 我们自己的验收口径。

这样模板一旦被多个项目复用，它就会从“参考材料”变成“组织级资产”。

---

## 方向二：把 Evals & Observability 升级成 TCD 的统一验收层

### 6.1 这是什么

把仓库中关于 eval、trace grading、observability、agent evaluation 的内容，转成 TCD 的统一验收和复盘机制。

简单说，就是建立一套可重复的规则来回答：
- 这个 workflow 到底有没有成功？
- 哪个节点最容易失败？
- 失败是因为模型、环境、工具、权限还是流程设计？
- 这次比上次更好还是更差？
- 成本、耗时、成功率、人工干预次数有没有下降？

### 6.2 为什么值钱

TCD 如果只有“能跑”，但没有“能测”，很快就会遇到天花板。

因为你会发现：
- 不同 workflow 都说自己能用；
- 但没有统一标准比较；
- 一次成功和长期稳定无法区分；
- 很多失败只停留在主观描述；
- 无法做真正的回归和对照。

而 eval / observability 正是把 TCD 从“经验方法论”推进成“工程系统”的关键。

### 6.3 可以吸收哪些内容

优先吸收：
- OpenAI 的 agent evals、trace grading；
- Anthropic 对 infrastructure noise、agent eval 的分析；
- LangChain 对 deep agents 评估的结构化经验；
- 任何能转成 task-level / trace-level / workflow-level 指标的内容。

### 6.4 最短落地形态

新增一个统一验收 schema，例如：

```text
evals/
  schemas/
    task_result.schema.json
    trace_grade.schema.json
    failure_taxonomy.schema.json
    session_metrics.schema.json
  scripts/
    summarize_results.py
    grade_trace.py
  examples/
    sample-eval-report.md
```

关键字段至少包括：
- 任务 ID
- 输入范围
- 预期目标
- 实际结果
- 成功 / 失败 / 部分成功
- 失败类型
- 工具调用统计
- 总耗时
- token / 成本
- 人工干预次数
- 是否可复现

### 6.5 对 TCD 的直接意义

一旦这层建立起来，TCD 就可以形成：
- 固定的验收出口；
- 固定的失败分类法；
- 固定的版本对比方式；
- 固定的复盘文档格式。

这会显著提升后续所有项目的稳定性和可比较性。

---

## 方向三：把 Specs / AGENTS / Agent Files 升级成 TCD 标准脚手架

### 7.1 这是什么

把仓库中关于 AGENTS.md、agent.md、spec-kit、12-factor agents 的内容，转成 TCD 的标准工程骨架。

这部分不是“参考一下别人怎么写 AGENTS”，而是要产出：
- 我们自己的全局规则；
- 仓库级规则模板；
- 任务规格模板；
- 验收出口模板；
- checkpoint / handoff / rollback 模板；
- commands / skills / hooks 的标准目录结构。

### 7.2 为什么这部分值钱

因为它天然就是组织级资产。

别人的文章只能告诉你：
- AGENTS 应该写什么；
- Specs 对 agent 有帮助；
- 标准文件有价值。

但真正能带来效率的，是：
- 团队内部已经形成一整套统一模板；
- 新项目不再从 0 开始决定结构；
- 所有人都在同一套工作语义里合作。

### 7.3 最短落地形态

做一个 `tcd-agent-standard-kit/`：

```text
tcd-agent-standard-kit/
  AGENTS.md
  TASK_SPEC.md
  CHECKPOINT.md
  DONE_CRITERIA.md
  HANDOFF.md
  FAILURE_REPORT.md
  commands/
  skills/
  hooks/
```

### 7.4 推荐包含的标准能力

至少要定义：
- 任务怎么写目标；
- 如何写范围边界；
- 如何写执行计划；
- 如何写真实验收；
- 如何写交接；
- 什么叫完成；
- 什么叫禁止假验收；
- 什么叫中断恢复；
- 什么情况下需要人工确认。

### 7.5 它和模板库的区别

模板库偏项目初始化。

标准脚手架偏组织规则和执行语义。

两者必须配合：
- 模板让项目能开工；
- 标准让项目不会乱。

---

## 方向四：把 Runtimes / Harnesses 升级成 TCD 工作流编排产品

### 8.1 这是什么

把 runtime / harness / workflow editor 相关内容，整合成 TCD 自己的编排层。

这部分不是简单画图，而是把“可视化工作流”真正接上：
- 子代理节点；
- 技能节点；
- MCP 节点；
- 分支节点；
- 人类确认节点；
- 验证节点；
- 回滚节点；
- 结束条件节点。

### 8.2 为什么它是中期最有产品护城河的部分

因为模板和标准会逐渐成为默认能力。
但编排层一旦做好，会直接成为：
- 项目管理入口；
- 任务执行入口；
- 自动化产线入口；
- 团队协作的可视化中枢。

这才是真正容易形成“我们自己的系统”的位置。

### 8.3 当前最适合承接的方向

现有 TCD 已有：
- `cc-wf-studio`
- `tcd-ui-insight`

说明这条线已经不是纯设想，而是有承接基础。

接下来最应该做的是收敛范围：
- 不要做通用工作流宇宙；
- 先做 TCD 专用编排器；
- 只支持 TCD 当前最常见的节点模型；
- 先保证“能导出可执行骨架”。

### 8.4 最短落地形态

输入：
- 任务描述
- feature list
- 模板类型
- 是否需要浏览器 / MCP / 验证 / 人工确认

输出：
- workflow JSON
- shell / node / python 执行骨架
- 验收脚本骨架
- handoff 文档骨架

### 8.5 这一步的商业含义

一旦工作流编排器成熟，TCD 就不只是“理念”或“脚手架集合”，而会变成：

> **一个可操作、可解释、可交接、可审计的 Agent 执行平台。**

---

## 方向五：把 Benchmarks 升级成 TCD 对照实验场

### 9.1 这是什么

不是自己重新造 benchmark，而是把 README 中已有 benchmark 转成 TCD 的实验适配层。

重点不在排行榜，而在对照：
- 裸 agent 的表现如何；
- 加入 TCD 模板 / 验收 / workflow 后表现如何；
- 哪种 harness 更稳；
- 哪种执行策略更省成本；
- 哪种验证链路更靠谱。

### 9.2 为什么值钱

因为所有方法论最后都会遇到同一个问题：

> 你说自己更好，有证据吗？

如果没有对照实验，TCD 很容易停留在经验和叙事层。

而 benchmark adapter 能提供：
- 对外证明；
- 内部优化目标；
- 回归基线；
- 版本比较依据。

### 9.3 优先接哪些 benchmark

建议优先级：
1. Terminal-Bench
2. SWE-bench Verified
3. WebArena / WebArena-Verified
4. OSWorld
5. MCPBench / MCPMark

这些最接近 TCD 要解决的真实任务类型。

### 9.4 最短落地形态

做一个：

```text
benchmark-adapters/
  terminal-bench/
  swe-bench/
  webarena/
  osworld/
  mcpbench/
```

统一输出：
- 任务结果
- trace 评分
- failure taxonomy
- 成本 / 耗时 / 成功率
- 对照实验报告

### 9.5 注意事项

不要一开始就追求“榜单成绩”。
那会把方向带偏。

前期真正应该追的是：
- 可复现；
- 可对照；
- 可解释；
- 可迭代。

---

## 六、哪些东西不值得优先做成产品

### 10.1 纯资讯镜像站

把文章翻译成中文、摘摘要、做导航页，这些都可以做，但不应该成为主产品方向。

原因很简单：
- 壁垒低；
- 很容易被替代；
- 很难直接转化为工程收益。

### 10.2 通用 leaderboard 聚合页

榜单链接可以保留，但不值得自己重做一个排行榜产品。

因为这类页面：
- 很容易看起来很热闹；
- 但很难形成自己的核心能力；
- 也很容易把注意力从“执行系统建设”带偏到“追榜”。

### 10.3 泛框架式 Agent 平台复刻

不要把这件事做成：
- 另一个 LangChain；
- 另一个 Agent SDK；
- 另一个 Workflow Universe；
- 另一个泛化 Agent IDE。

这不是 TCD 的最短路径。

TCD 的优势从来不是“框架最全”，而是：
- 执行更稳；
- 结构更清晰；
- 验收更真实；
- 交接更自然；
- 经验更容易沉淀。

### 10.4 只做 benchmark 摘抄

如果 benchmark 只是挂链接，那它的价值很低。

只有当 benchmark 被改造成：
- 可接入；
- 可跑；
- 可输出统一结果；
- 可比较不同 harness；

它才真正有用。

---

## 七、建议的落地路线图

### 第一阶段：研究仓 → 模板仓

目标：先把资料转成模板，不要空谈平台。

重点交付：
- 模板目录结构
- 多种项目初始化模板
- handoff / acceptance / init / check 模板
- README 中的“TCD 融合”入口

阶段产出：
- 任何新项目都能直接从模板起步；
- 资料不再只停留在阅读层。

### 第二阶段：模板仓 → 标准仓

目标：把模板和规则升级成统一标准。

重点交付：
- TCD Agent Standard Kit
- AGENTS / TASK_SPEC / DONE_CRITERIA 等标准文件
- commands / skills / hooks 的建议骨架

阶段产出：
- 团队级一致性明显增强；
- 不同项目之间更容易迁移、接手、复用。

### 第三阶段：标准仓 → 验收仓

目标：让执行结果可测、可比、可复盘。

重点交付：
- eval schema
- trace grading
- failure taxonomy
- 汇总与复盘脚本

阶段产出：
- 可以开始用真实结果说话；
- 可以判断哪些 workflow 真稳定、哪些只是偶然成功。

### 第四阶段：验收仓 → 编排器

目标：把模板、标准、验收链接入可视化编排层。

重点交付：
- workflow builder
- 节点语义标准化
- workflow 到执行骨架的导出能力

阶段产出：
- TCD 开始拥有真正的“系统操作面板”；
- 不再只是文档 + 脚本碎片集合。

### 第五阶段：编排器 → 基线实验场

目标：用 benchmark adapter 做外部证明和内部迭代。

重点交付：
- benchmark adapters
- 对照实验报告
- 版本演进对比面板

阶段产出：
- TCD 有了可验证的性能与稳定性证明；
- 后续对外表达不再停留在口头叙事。

---

## 八、建议在当前仓库中立刻追加的目录方向

为了让这个方案不是停留在纸面上，建议后续按以下方向扩展当前仓库：

```text
awesome-harness-engineering/
├── README.md
├── TCD_FUSION_PLAN.md
├── assets/
│   ├── templates/
│   ├── standards/
│   ├── eval-schemas/
│   └── benchmark-adapters/
├── notes/
│   ├── article-digests/
│   ├── extraction-notes/
│   └── mapping/
└── examples/
    ├── coding-agent-project/
    ├── research-agent-project/
    └── browser-agent-project/
```

其中：
- `assets/templates/`：存真正能被复制使用的模板；
- `assets/standards/`：存 TCD 标准化文件；
- `assets/eval-schemas/`：存统一验收结构；
- `assets/benchmark-adapters/`：存 benchmark 对接层；
- `notes/`：存研究到资产的中间转译笔记；
- `examples/`：存最小可跑的样例工程。

---

## 九、对这个仓库的最终定位建议

建议把这个仓库的定位明确成下面这句话：

> **它不是一个“AI Agent 资料收藏夹”，而是 TCD 的上游研究地图与资产转译入口。**

换句话说，它应该承担两个角色：

### 角色 1：上游研究入口
负责回答：
- 这个领域最近有哪些关键文章、标准、runtime、benchmark？
- 哪些资料值得读？
- 哪些方向值得继续追？

### 角色 2：下游资产转译入口
负责回答：
- 这些资料能被转成什么模板？
- 能形成什么标准文件？
- 能变成什么 workflow 节点？
- 能落成什么 eval schema？
- 能接到什么 benchmark adapter？

如果两个角色都做起来，这个仓库的价值会远高于普通 awesome list。

---

## 十、最后的判断

如果只是把 remote 改掉，然后继续往 README 里补链接，这个仓库不会真正产生战略价值。

真正有战略价值的做法，是把它作为：
- TCD 研究输入层；
- TCD 模板抽取层；
- TCD 标准沉淀层；
- TCD 验收与实验层；
- TCD 工作流编排的知识上游。

最终要达到的状态不是：
- “我们也有一个 awesome list”。

而是：
- “我们有一套能持续把上游 harness engineering 知识，翻译成可执行工程资产的系统。”

这才是“变成我们自己的”的真正含义。
