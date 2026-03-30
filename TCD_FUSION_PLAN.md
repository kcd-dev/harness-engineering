# TCD × Harness Engineering 融合方案

## 目标

这个仓库不该只停留在“awesome list”。
真正值钱的部分，是把这里的 harness engineering 资料沉淀成 **TCD 可执行资产**：模板、命令、工作流、评测面板、基线仓库、可视化编排器。

一句话：

> 别只做资料导航站，要把高价值方法论翻译成 TCD 的可执行系统。

---

## 优先级 1：把「资料索引」升级成 TCD 的执行模板库

### 融合方式
把 README 里的高价值条目，按 TCD 结构拆成可复用模板：

- `init.sh` / 环境预检模板
- `feature_list.json` / 功能清单模板
- `workflow.json` / 任务状态模板
- `check.sh` / 验证脚本模板
- `handoff.md` / 长任务交接模板

### 为什么值钱
因为用户真正缺的不是“知道有这篇文章”，而是：

- 怎么开新项目
- 怎么初始化 harness
- 怎么做长任务断点续跑
- 怎么做交接和验收

这些一旦模板化，就能直接复用到 TCD 各项目。

### 最短落地形态
做一个 `templates/` 目录：

- `coding-agent-project/`
- `research-agent-project/`
- `browser-agent-project/`
- `eval-first-agent-project/`

每个模板都对应一套最小可跑的 TCD 初始化骨架。

---

## 优先级 2：把「Evals & Observability」升级成 TCD 的验收/复盘引擎

### 融合方式
将 OpenAI / Anthropic / LangChain 关于 eval、trace grading、observability 的资料，转成 TCD 的标准验收层：

- 任务级验收清单
- trace 评分维度
- 错误分类标签
- 回归测试入口
- 成本/耗时/成功率统计

### 为什么值钱
TCD 现在已经强调“程序执行”，下一步就必须补上：

- 怎么判断脚本真的好用
- 怎么知道哪一步最容易坏
- 怎么比较不同 workflow 的效果

这部分直接决定 TCD 能不能从方法论升级成工程系统。

### 最短落地形态
做一个 `evals/` 目录和统一 JSON schema：

- `task_result.json`
- `trace_grade.json`
- `failure_taxonomy.json`
- `session_metrics.json`

再配一个最小汇总脚本，把批量任务跑完后的结果汇总成 Markdown 报告。

---

## 优先级 3：把「Specs / AGENTS / Agent Files」升级成 TCD 的标准项目脚手架

### 融合方式
把 README 里关于 AGENTS.md、agent.md、spec-kit、12-factor agent 的内容，收敛成 TCD 的工程骨架：

- 全局 AGENTS 规则
- 仓库级 AGENTS 模板
- task spec 模板
- handoff / checkpoint 模板
- command / skill / hook 组织规范

### 为什么值钱
这部分最适合变成我们自己的标准。
因为它天然属于“组织资产”和“团队操作系统”，不是单篇文章能替代的。

### 最短落地形态
产出一个 `tcd-agent-standard-kit/`：

- `AGENTS.md`
- `TASK_SPEC.md`
- `CHECKPOINT.md`
- `DONE_CRITERIA.md`
- `commands/`
- `skills/`

让任何新项目 10 分钟内完成标准化落地。

---

## 优先级 4：把「Runtimes / Harnesses」升级成 TCD 的工作流编排产品

### 融合方式
结合现有 `cc-wf-studio` / `tcd-ui-insight` 方向，不再只展示 workflow，而是做成 TCD 的可执行编排器：

- 子代理节点
- Skill 节点
- MCP 节点
- 条件分支节点
- 人类确认节点
- 验证节点
- 失败回滚节点

### 为什么值钱
因为这部分是最容易形成产品护城河的。
awesome list 只是别人资料的集合；
可视化编排 + TCD 执行标准，才是自己的系统资产。

### 最短落地形态
先不要做大而全平台。
先做一个只服务 TCD 的 workflow builder：

- 输入：任务描述 / feature_list / 现有模板
- 输出：可执行 workflow JSON + shell/python/node 脚本骨架

也就是把“AI 做翻译，程序做执行”落到可视化层。

---

## 优先级 5：把「Benchmarks」升级成 TCD 的基线仓与对照实验场

### 融合方式
不是自己造新 benchmark，而是把现有 benchmark 转成 TCD 的对照实验环境：

- Terminal-Bench
- SWE-bench
- WebArena
- OSWorld
- MCPBench

重点不是追榜，而是建立：

- 哪种 harness 结构更稳
- 哪种 prompt / workflow 更省 token
- 哪种验证链路更靠谱

### 为什么值钱
因为 TCD 想证明自己，不靠嘴，靠对照实验。
这部分会成为后续所有“我们的方案比通用 agent 框架更稳”的证据库。

### 最短落地形态
建一个 `benchmark-adapters/`：

- 每个 benchmark 一个 adapter
- 统一输出 TCD eval schema
- 可以对比“裸 agent vs TCD harness”

---

## 明确不值得做的东西

以下内容适合保留为资料索引，但 **不值得优先产品化**：

### 1. 纯资讯型文章镜像
像 Foundations 里很多概念文章，适合做阅读入口，不适合做产品主体。
因为信息价值高，但复用壁垒低。

### 2. 通用 leaderboard 聚合页
Agent Arena、HAL、Galileo 这些可以保留链接，但没必要自己重做一个排行榜站。
这事流量看着大，实际不形成 TCD 核心资产。

### 3. 泛化 agent framework 搬运
LangChain / Agent SDK / deepagents 这些适合研究，不适合直接当我们的主产品。
否则会重新掉回“做一个大而泛的 agent 平台”，偏离 TCD 的最短路径。

### 4. 纯论文式 benchmark 摘抄
只收录 benchmark 没价值。
只有接成 TCD 的可执行实验场，才值钱。

---

## 建议的产品化顺序

1. **模板库**：先把资料转成可执行模板
2. **验收层**：把 eval / trace / metrics 做起来
3. **标准脚手架**：沉淀成 TCD Agent Standard Kit
4. **工作流编排器**：把 TCD 变成真正可视化系统
5. **Benchmark Adapter**：最后补对照实验和外部证明

---

## 最终判断

这个仓库最该做的，不是“继续加链接”。
而是把高信号资料拆成：

- **模板**
- **标准**
- **工作流**
- **评测**
- **对照实验**

这样它才会从一个 curated list，变成 TCD 体系里的上游研究入口 + 下游工程资产生成器。
