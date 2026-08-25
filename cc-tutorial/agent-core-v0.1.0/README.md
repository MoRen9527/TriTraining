# agent-core v0.1.0 四版渐进式教程（Claude Code 移植骨架）

## 文档同步元信息

- sourceOfTruth: TriTraining/cc-tutorial/agent-core-v0.1.0/README.md（本目录索引；代码事实真源见下"代码事实真源"节）
- syncMode: source-derived（教程内容派生自 agent-core v0.1.0 源码快照）
- lastSyncedAt: 2026-08-25
- tutorialVersion: agent-core-v0.1.0

## 本目录是什么

四份由浅入深的教程，讲解 TriCompany 把 Claude Code 2.1.88 核心能力以"种子资产重实现"路线移植成的自研内核 **@tricompany/agent-core v0.1.0**。

| 文件 | 定位 | 读者与目标 |
| --- | --- | --- |
| [01-小白版.md](01-小白版.md) | 快速了解入门 | 零基础同事：agent-core 是什么、公司为什么自研（对照原版 CC）、核心概念白话词典、一张全景图 |
| [02-产品版.md](02-产品版.md) | 从产品入手 | 产品/运营视角：能力清单与应用场景、在产品栈中的 M/R 双面位置、与直接用 CC 的差异和取舍、典型流程走查 |
| [03-代码引导版.md](03-代码引导版.md) | 快速捋代码结构 | 新接手工程师：仓库导览、模块地图、一次请求的端到端时序、如何跑起来与调试 |
| [04-代码复刻版.md](04-代码复刻版.md) | 详细代码逻辑研究 | 目标读者看完能自己动手复刻：逐模块函数级逻辑、数据结构、调用关系、边界条件与已知缺口、复刻步骤清单 |

建议阅读顺序即编号顺序；每一版都在结尾指向下一版。只关心"这东西干嘛的"读 01 即可；要接手代码至少读到 03；要在内核上做改动或自己复刻一套，精读 04。

## 版本规则（重要）

- **本目录绑定 agent-core v0.1.0**（`packages/agent-core/package.json` 的 `version: 0.1.0`）。
- 内核升版后**新建平行目录**（如 `cc-tutorial/agent-core-v0.2.0/`）出新一版四件套；**旧版本目录冻结归档，不再就地修订**。
- 教程中的行号引用对应该版本的源码快照；升版后行号会漂移，以新目录的新版教程为准。

## 代码绑定（fingerprint，2026-08-25 采集）

教程内容精确锚定到以下源码状态——**任何一项不匹配即视为代码已漂移**：

| 绑定项 | 值 |
| --- | --- |
| 承载仓 | TriCompany |
| 绑定提交 | `3c3cee1bfe74fa1946980f879940235e2355196c` |
| agent-core 目录树哈希 | `d90121d41f5f22c512ec73d01ccb6c7e89c30677`（`git rev-parse HEAD:packages/agent-core`） |
| agent-core 最近实质提交 | 2026-08-25 16:17 +0800 |
| 包版本 | 0.1.0 |

校验命令：`git -C TriCompany rev-parse <绑定提交>:packages/agent-core`——输出等于上表树哈希即代码未漂移；不一致则本教程描述的是历史快照。

### 漂移后的更正流程

1. **小漂移**（个别文件改动）：对照新旧树哈希 `git diff <旧树哈希> <新树哈希>` 逐文件勘误本目录教程，原地修正并在各文件元信息头追加「勘误 as-of 日期」；不改目录名。
2. **大漂移**（包版本 bump / 结构性重构 / 行为语义变化）：新建平行目录出新一版四件套，旧版冻结。
3. 更正时同步补上新增源码的讲解（"更正教程也对补上源码"，CEO 2026-08-25）。

## 代码事实真源

教程不是真源，只是导览。所有论断请回到以下真源核对：

- 内核源码：`TriCompany/packages/agent-core/src/`（40 个 TS 文件，8 个源码区）
- 现役消费者 A：`TriLC/src/server/app.ts`（daemon HTTP 面，`/v1/messages` 与 `/internal/v1/agent` 直接跑 agentLoop）
- 现役消费者 B：`TriRMC/`（`package.json` 以 `file:../TriCompany/packages/agent-core` 引入；`src/agent-loop/loop.ts` 为薄壳 DI 层）
- CC 原版机制对照与创新记录：`TriCompany/docs/engineering/claude-code-spawn-resume-context-innovation-record.md`
- 种子资产迁移语境（七大件清单与批项）：`TriMetaverse/docs/workflow/tricompany-handoff-objects.md` 所在 workflow 域 + `TriRMC/MIGRATION.md`
- 合同 v3 规格：`TriCompany/docs/engineering/agent-contract-v3-spec.md`

## 使用依据

- 本文目录结构遵循 TriTraining 模块基线（`TriTraining/AGENTS.md`、`docs/training/`）。
- 四版教程的每个代码论断均标注 `文件路径:行号`，对应 agent-core v0.1.0 快照。
