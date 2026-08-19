# 白话讲解员工发布全链路：source → support → binding → live → manifest → governance

## 文档同步元信息

- sourceOfTruth: TriTraining/docs/training/employee-host-publish-chain-beginners-guide.md
- publishedFrom: TriTraining/docs/training/employee-host-publish-chain-beginners-guide.md
- syncMode: module-source
- publishTier: module-training-course
- lastSyncedAt: 2026-08-19

版本：V0.1
日期：2026-08-19
状态：新员工 onboarding 白话课程；补齐「当前 Copilot-host 支撑包和 live 宿主入口」待补培训主题（见 `TriCompany/docs/training/README.md` 与 `TriMetaverse/docs/training/README.md` 待补清单）；以 Copilot 宿主为当前现状，多宿主渲染模型为规划中（见第 10 节）

## 1. 这门课讲什么

TriCompany 里每上一个「AI 员工」，都要走一条发布链。以前有一门课讲过这条链的前三环（[source -> support -> binding](employee-host-publish-pipeline-course.md)），本课把整条链补全：**source → support → binding → live → manifest → governance** 六环，一个都不少。

本课面向两类读者：

1. **新员工 onboarding**：你刚进 TriCompany，想知道「我在这个组织里是怎么被定义、被发布、被宿主发现的」。
2. **研发 onboarding**：你要接手发布相关代码或流程，需要知道「改哪里、发哪里、验哪里、回哪里查」。

学完本课后，你应该能不看文档、用大白话复述出：六环各自是什么、文件在哪、一个员工怎么走完一整条链、卡住时回哪个真源查。

重要约定：本课讲的「现状」都以 **Copilot 宿主**为例——这是当前已实现的发布形态。未来要多宿主渲染、binding 派生化、live entry 渲染化（见第 10 节）都还处于**规划中**，本课不把它们写成已实现。

## 2. 先看大结果：六环全貌

把「一个 AI 员工入职到 Copilot 宿主」想成真人入职，六环就很好记：

| 环 | 白话比喻 | 真实位置 | 一句话职责 |
| --- | --- | --- | --- |
| 1. source | 人事档案原件 | `TriCompany/source-agents/<employee-id>/` 五件套 | 员工是谁：岗位契约 |
| 2. support | 工位 + 办公系统 | `TriMetaverse/TriCompany-copilot-host-assets/` 知识工作区 | 员工干活用的知识放哪 |
| 3. binding | 工牌上的绑定信息 | `TriCompany/.github/binding-profiles/<employee-id>.json` | 当前绑在哪个宿主 |
| 4. live | 前台名册上的唯一名字 | `TriMetaverse/.github/agents/<employee-id>.agent.md` | 宿主怎么发现你 |
| 5. manifest | 两份台账 | 源侧生成清单 + support 登记清单 | 生成规则和已发对象怎么查 |
| 6. governance | HR / 行政 / 专业 owner 回填验收 | 角色回填记录 | 谁确认你正式上岗 |

最终效果：**一个员工从「源侧定义」到「宿主可发现、可验收」，每一步都有明确落点、有台账、有真源**。新人接手时，任何一个环节都能回答「这是谁写的、在哪、怎么改、怎么验」。

本课与已有的 [source -> publish -> live 链路白话课](../training/tricompany/03-source-publish-live-链路.md)（在 TriMetaverse 仓）的关系：那门课讲的是「四层承载面」的资产分工（source truth / support bundle / live entry / central summary），本课讲的是「六环发布链」的流动顺序。两门课互补：先懂四层在哪，再懂六环怎么走。

## 3. 价值：为什么是六环，而不是一个目录

每一个环回答一个问题，少一环就会出事故：

1. **source** 回答「员工是谁」——如果只有 live 没有 source，员工定义就没有真源，谁都能改 live 文件，漂移失控。
2. **support** 回答「知识放哪」——如果知识直接塞进 source 或 live，运行数据和岗位契约就混在一起。
3. **binding** 回答「当前绑在哪个宿主」——没有它，换宿主时无从知道当前 stage 和 live 入口是谁。
4. **live** 回答「宿主怎么发现你」——入口不唯一，宿主不知道该调谁。
5. **manifest** 回答「规则和对象怎么查」——没有台账，发过什么、谁生成的、按什么规则生成的，全凭记忆。
6. **governance** 回答「谁验收」——没有回填，发布链跑完没人确认，历史也追不到。

所以六环的本质是**六个职责分离的落点**，每环只做一件事，方向单向：`source → support → binding → live → manifest → governance`，禁止反向长期维护（详见 `TriCompany/docs/workflow/host-object-publish-flow.md` 与 `TriMetaverse/docs/workflow/tricompany-copilot-host-assets-governance.md`）。

## 4. 理论方法与协议（白话版）

### 4.1 三条铁律

1. **单向发布**：事实从源侧定义出发，向 support、live 单向发布；support / live 发现真源缺失或漂移时，改回 source，不在发布侧长期反写。
2. **契约 / 载荷 / 绑定分层**：源侧五件套只放岗位契约；support payload 是宿主消费面；binding profile 只记录当前宿主绑定事实，不替代 live discovery。
3. **验证先行**：发布链必须有验证命令和 workflow 文档约束；「生成成功」不等于「live 已自动启用」，也不等于「TriMC 正式宿主切换」。

### 4.2 发布顺序主纲（11 步，白话压缩版）

真源主纲见 `TriCompany/docs/workflow/host-object-publish-flow.md` §2，这里压缩成 6 个动作：

1. **确认变更类型**：新入职 / 职责变动 / owner 迁移 / 五件套增量更新。
2. **改或生成 source 五件套**：`TriCompany/source-agents/<employee-id>/` 下 agent / soul / memory / colleagues / social 五件套（新员工用 source kit scaffold 生成）。
3. **源侧 validator 检查**：确认五件套只含岗位契约，没有运行消费记录、没有宿主 binding marker。
4. **生成 support 对象 + 登记 manifest**：跑 host object generator / publish wrapper，产出 knowledge 工作区和 `host-object-manifest.json`。
5. **导出 binding profile + 判断 live 入口**：生成 `binding-profiles/<employee-id>.json`；live 入口唯一，已有现役入口则复用不新建。
6. **治理回填**：CHO handoff checklist / CAO 秘书处治理 / 对应专业 owner 验收记录。

### 4.3 关键命令（在 `TriCompany/` 仓库根执行）

```powershell
# 新员工：生成源侧五件套模板
python -m runtime.cognition.employee_source_kit generate --source-root . --employee-id customer-success-officer --agent-name CustomerSuccessOfficer --display-name "小成" ...

# 统一发布 wrapper（canonical 入口：support payload + binding profile 一把出）
python -m runtime.cognition.employee_host_publish --source-root . --support-root ..\TriMetaverse\TriCompany-copilot-host-assets --employee customer-success-officer

# 全量刷新（--employee all 慎用，先确认增量门禁）
python -m runtime.cognition.employee_host_publish --source-root . --support-root ..\TriMetaverse\TriCompany-copilot-host-assets --employee all

# 验证
python -m unittest runtime.cognition.employee_source_kit_validation runtime.cognition.role_employee_workspace_validation runtime.cognition.employee_host_binding_profile_generation_validation
```

注意：`employee_host_publish` 是 wrapper，会同时产出 support payload 与 binding profile；但**它不自动启用 live agent**，live 入口是否新增 / 复用仍要走判断（发布顺序第 10 步）。

## 5. MVP 全流程：用小成（CustomerSuccessOfficer）走一遍

我们拿真实员工「小成」（CustomerSuccessOfficer，客户成功负责人）当例子，把六环走一遍。他的发布属于 W33 ADE onboarding（w33-3），在源侧生成清单和 support 登记清单里都有记录，可直接对照。

| 步 | 环节 | 产物（真实路径） | 一句话说明 |
| --- | --- | --- | --- |
| 1 | source | `TriCompany/source-agents/customer-success-officer/{agent-body,agent-frontmatter,soul,memory,colleagues-social}.agent.md` + `customer-success-officer.contract.yaml` | 小成的源侧员工契约（注意：小成是早期员工，五件套文件命名不是标准五件套名，但语义一致） |
| 2 | support | `TriCompany-copilot-host-assets/knowledge/roles/customer-success-officer/**`、`knowledge/employees/customer-success-officer/**`、`knowledge/org/shared/**`、`knowledge/audit/**` | 岗位知识区 + 员工知识区 + 全公司共享区 + 审计区 |
| 3 | binding | `TriCompany/.github/binding-profiles/customer-success-officer.json` | 声明 hostStage=current-copilot-host-live、liveEntry 路径、supportObjects 清单 |
| 4 | live | `TriMetaverse/.github/agents/customer-success-officer.agent.md` | 唯一 live discovery 入口，宿主从这里发现小成 |
| 5 | manifest | 源侧 `TriCompany/.github/manifests/tricompany-host-object-generation-manifest.json`（objectSetId `customer-success-officer-knowledge-workspace-v0.1`）+ support 侧 `TriCompany-copilot-host-assets/host-object-manifest.json` | 生成规则台账 + 已发对象登记台账；另外 live 环还配套一份 `TriCompany/source-agents/registries/trimetaverse-live-agent-publish-manifest.json` 登记每个 live entry 的 target/source 对应 |
| 6 | governance | W33 ADE onboarding 记录（w33-3）+ binding profile notes | 小成按当前 Copilot-host live 上岗，记录在案 |

最小闭环验证（在 `TriCompany/` 根执行）：

```powershell
python -m unittest runtime.cognition.role_employee_workspace_validation runtime.cognition.employee_host_binding_profile_generation_validation
```

跑完你就拿到了发布链的最小事实：support 对象生成、binding profile 落位、live entry 断言都在。

## 6. 六环逐个拆解

### 6.1 source 环：源侧员工契约

- **是什么**：员工的「人事档案原件」——岗位是谁、气质如何、记忆分层、协作关系、社交边界，共五件套（agent / soul / memory / colleagues / social）。
- **在哪**：`TriCompany/source-agents/<employee-id>/`。注意：**它不是 live 入口**，宿主不会从这里发现员工；放在源侧是为了避免 IDE 把源侧草稿当成 live agent。
- **谁负责**：TriCompany 源侧 owner（当前阶段由 CEOChiefOfStaff 协调，专业边界回 CHO / 专业 owner）。
- **怎么走**：新员工用 `employee_source_kit generate` 生成模板，再跑 `validate`；现有员工直接更新对应五件套文件。
- **怎么验证**：`python -m unittest runtime.cognition.employee_source_kit_validation`。validator 会检查：五件套齐全、不含运行消费记录标记、不含「当前 live 入口位于」这类宿主 binding marker。
- **真源**：`TriCompany/docs/workflow/host-object-publish-flow.md` §3；`TriCompany/docs/workflow/rd-trainer-role.md`（岗位定义样例）。

### 6.2 support 环：宿主支撑包

- **是什么**：当前 Copilot 宿主的「工位和办公系统」——员工上岗后干活用的知识工作区。
- **在哪**：`TriMetaverse/TriCompany-copilot-host-assets/`（物理在 TriMetaverse 仓下）。知识工作区四类：`knowledge/roles/<employee-id>/**`（岗位知识，可继承）、`knowledge/employees/<employee-id>/**`（员工知识，当前实例连续性）、`knowledge/org/shared/**`（全公司共享）、`knowledge/audit/**`（审计痕迹）。
- **谁负责**：从 TriCompany 源侧通过 host-object 发布流程单向生成；当前阶段由 CEOChiefOfStaff 协调，技术内容由 TriCompanyCodeRegistry 护栏。
- **怎么走**：跑 `employee_host_object_generation` 或统一 wrapper `employee_host_publish`。
- **怎么验证**：`python -m unittest runtime.cognition.role_employee_workspace_validation`；对照 `TriCompany-copilot-host-assets/host-object-manifest.json` 登记是否反映最新 object set。
- **真源**：`TriCompany/docs/workflow/host-object-publish-flow.md` §4；`TriMetaverse/docs/workflow/tricompany-copilot-host-assets-governance.md`（四层资产模型）；`TriMetaverse/docs/workflow/tricompany-copilot-host-assets-migration-matrix.md`（状态标签：support-object-set / runtime-state 等）。

### 6.3 binding 环：当前宿主绑定事实

- **是什么**：「工牌绑定信息」——当前 host stage、live entry、support object 映射、runtime namespace，全部是**当前宿主绑定事实**，不是岗位契约本身。
- **在哪**：`TriCompany/.github/binding-profiles/<employee-id>.json`（以小成为例：`customer-success-officer.json`）。
- **谁负责**：由 `employee_host_binding_profile_generation` 基于源侧声明的 `HostObjectSetDefinition` 显式导出，**不人工编辑**。
- **怎么走**：改完 source 定义后，重新生成 binding profile 跟随。
- **怎么验证**：`python -m unittest runtime.cognition.employee_host_binding_profile_generation_validation`。
- **真源**：`TriCompany/.github/manifests/tricompany-host-object-generation-manifest.json`（声明生成规则与 binding 索引）；`TriCompany/docs/workflow/host-object-publish-flow.md` §2（第 9 步）。

### 6.4 live 环：唯一 live discovery 入口

- **是什么**：宿主「前台名册上的名字」——Copilot 宿主实际能发现、能调用的唯一入口文件。
- **在哪**：`TriMetaverse/.github/agents/<employee-id>.agent.md`（当前 live 面）。小成入口：`TriMetaverse/.github/agents/customer-success-officer.agent.md`。
- **谁负责**：live 入口只做当前宿主入口的吸收、替换、回滚和验证；不承担模块实现细节研发。
- **怎么走**：发布顺序第 10 步——判断是否需要新增 / 更新 live 入口；**已有现役入口则复用，不新建第二个 discoverable agent**（如 CPO / CTO / CEOChiefOfStaff 都是复用现役入口）。
- **怎么验证**：对照 `TriCompany/source-agents/registries/trimetaverse-live-agent-publish-manifest.json` 的 liveEntries：每个员工只有一条 target，`status` 为 `current-copilot-host-live`，且 source 指向源侧五件套。
- **真源**：`TriCompany/source-agents/registries/trimetaverse-live-agent-publish-manifest.json`；`TriCompany/docs/workflow/host-object-publish-flow.md` §3（agent discovery 口径）。

### 6.5 manifest 环：两份台账

- **是什么**：发布链的「台账」。注意是**两份**，别搞混：
  1. **源侧生成清单**：`TriCompany/.github/manifests/tricompany-host-object-generation-manifest.json`——声明「按什么规则生成、每个员工的对象集包含哪些 source 定义、binding profile 和 support 对象路径」，是生成规则的声明。
  2. **support 登记清单**：`TriCompany-copilot-host-assets/host-object-manifest.json`——登记「实际已发布的对象集」，每条含 objectSetId、generatedAt、generator、sourceRefs、supportObjects、runtimeNamespaces，是已发对象的登记。
- **在哪**：见上，两份物理路径不同（一份在 TriCompany 源侧，一份在支撑包）。
- **谁负责**：源侧清单在岗位 / 员工定义确认后显式登记；support 清单由生成器 upsert。
- **怎么走**：发布顺序第 7、8 步——先确认源侧声明，再登记 support 对象。
- **怎么验证**：两清单的 objectSetId、bindingProfile 路径、supportObjects 路径应互相咬合。
- **配套第三份**：live 环还配一份 `trimetaverse-live-agent-publish-manifest.json`（在 `TriCompany/source-agents/registries/` 下），登记每个 live entry 的 target / source / status / kind，是 live discovery 的发布清单。
- **真源**：两份 manifest 本身；`TriCompany/docs/workflow/host-object-publish-flow.md` §2（第 7、8 步）。

### 6.6 governance 环：角色回填验收

- **是什么**：发布链的最后一环——**角色回填**，不是改治理文档。即：CHO handoff checklist、CAO 秘书处治理、对应专业 owner 验收（产品变 CPO、技术变 CTO、岗位变 CHO、治理文档归属变 CAO、中央战略升级 CEO / BusinessStrategy）。
- **在哪**：回填记录落在各 owner 的治理 / handoff 记录中；调试阶段记录为当前阶段验收，成熟后必须按授权矩阵留下签字或等价批准。
- **谁负责**：CHO（handoff checklist 设计与完成度监督）、CAO / CompanyGovernanceRegistry（秘书处与行政制度）、对应专业 owner（专业验收）；CEOChiefOfStaff 保留公司级协调、催办、升级与收口。
- **怎么走**：发布顺序第 11 步；涉及岗位 / 职责交接时，CHO 设计 handoff checklist 并监督完成度。
- **怎么验证**：handoff / completion tracking 是否进入 `ready-for-acceptance` 或 `accepted`；无法判断时应标 `待确认` / `blocked`，不得写成已完成 live 变更。
- **真源**：`TriCompany/docs/workflow/host-object-publish-flow.md` §2（第 11 步 + 补充治理）；CHO handoff 治理文件（`TriCompany/docs/workflow/chief-human-resources-officer-handoff-governance.md` 等）。

## 7. 心智模型：一张纸复述六环

**一句话版**：`source 定义人 → support 放知识 → binding 记绑定 → live 被发现 → manifest 留台账 → governance 做验收`。

**六个「不」**（每个都对应真实踩过的坑）：

1. source 不是 live 入口（五件套留在 `source-agents/`，不进 `.github/agents/`）。
2. support 不是第二真源（知识对象单向生成，规则变更回 source）。
3. binding 不是 live 本身（binding 记录绑定事实，live 才是发现入口）。
4. live 必须唯一（一个员工只有一个 discoverable 入口；已有现役入口就复用）。
5. manifest 分两份（源侧生成清单管「规则」，support 登记管「已发对象」，别混）。
6. governance 是回填不是改文档（验收、handoff、签字记录，不是修改治理文档本身）。

## 8. 常见误区

| 误区 | 正解 |
| --- | --- |
| 「员工五件套在 `source-agents/`，宿主应该能发现它」 | 不能。源侧五件套是契约，不是 live discovery 入口；宿主只从 live 入口发现员工 |
| 「support 包里的文件坏了直接改 support」 | 不行。support 是单向发布产物；规则改动回 source，再重跑发布 |
| 「binding profile 我手改一下就行」 | 不行。binding 由生成管线导出，人工编辑会造成漂移 |
| 「生成成功 = live 已启用」 | 不对。`employee_host_publish` 不自动启用 live；live 入口要单独判断（复用或新增） |
| 「manifest 只有一份」 | 不对。源侧生成清单 + support 登记清单是两份，另配 live 发布清单一份 |
| 「当前 Copilot-host live 上岗 = TriMC 正式宿主切换」 | 不对。这是当前 Copilot 宿主阶段的 live enablement，不是 TriMC 正式切换 |

## 9. 学习路径（先读什么、后读什么、每步验证）

1. **先看全貌**：本课第 2 节六环表 + [source -> publish -> live 链路白话课](../training/tricompany/03-source-publish-live-链路.md)（四层资产模型）。验证：能说出六环名字和每环一句话职责。
2. **再读主流程**：`TriCompany/docs/workflow/host-object-publish-flow.md` §2（11 步发布顺序）。验证：能复述 6 个压缩动作。
3. **看一份真实案例**：小成走全链（本课第 5 节），对照 binding profile 和两份 manifest 里小成的 objectSet。验证：能指出小成的 6 个落点文件路径。
4. **再看治理**：`TriMetaverse/docs/workflow/tricompany-copilot-host-assets-governance.md`（四层资产模型 + 单向发布纪律）+ `tricompany-copilot-host-assets-migration-matrix.md`（状态标签）。验证：能说出 source-only / support-object-set / live-entry / runtime-state 各指什么。
5. **最后接代码**：已有课程 [source -> support -> binding](employee-host-publish-pipeline-course.md) 的代码拆解顺序（wrapper → definition → generation → binding → validation）+ `TriCompany/runtime/cognition/` 下 `employee_source_kit.py`、`employee_host_object_generation.py`、`employee_host_binding_profile_generation.py`、`employee_host_publish.py`。验证：能说出 wrapper 与底层命令的关系，能跑通第 5 节的验证命令。
6. **下一步进阶**：规划中的多宿主渲染模型（第 10 节）落地后，本课需要随 ADE-B 执行同步更新。

## 10. 规划中内容（尚未实现，标注清楚）

以下内容**不是当前现状**，是 2026-08-19 CEO 已采纳、待分阶段执行的规划（真源：`TriCompany/docs/engineering/ade-consolidation-proposal.md` v1.0，状态「CEO 已采纳（2026-08-19），待分阶段执行」），任何情况下不得写成已实现：

1. **多宿主统一渲染模型**：员工发布到宿主侧将改为「源单份 + 每宿主渲染模板 → 渲染」，发布 CLI 增加 `--host={copilot|claude}`；Copilot-host 面（`.github/agents/`）与 Claude Code 面（`.claude/agents/`）将成为 contract 派生物，双源漂移从机制上消失。当前仍是「源侧五件套 + 发布侧拷贝式 live entry」形态。
2. **binding profile 派生化**：binding-profiles 与 agent contract 字段重叠部分将收敛——语义真源收 contract、绑定事实收 manifest，binding profile 保留为绑定快照但**禁人工编辑、由生成管线重建**。当前 binding profile 仍由生成管线导出（现状一致），但字段收敛与一致性校验未执行。
3. **live entry 渲染化**：live entry 定性为 contract 的派生加载壳 / 渲染产物，禁人工编辑，host 附加段须模板化回归源侧。当前 live entry 仍可人工编辑（现状）。
4. **知识注入消费链路缺口**：三端（研发仓 / TriLC / TriMC）当前均无知识注入功能——knowledge 资产处于「只生成、无消费」状态，消费方 Copilot-host 未激活。这是 ADE-B 阶段 1/2 工作包，记入 FADE-ASSESS-003。
5. **runtime 侧部署模型**：TriMC / TriLC 将不渲染、contract 直读（roster.active 即上岗）；当前仅宿主侧形态存在。
6. **安全默认与白名单反向校验**：`employee_host_publish` 当前无 `--dry-run`/`--execute` 时默认执行写入（违反安全门默认 dry-run 的规划要求）；`--publish-agents` 白名单缺反向禁区校验。这两处合同级缺口是 ADE 整合阶段 0 待修项。

另外说明：`sync-agents-to-claude.mjs` 是 Claude Code 侧的过渡机制（Claude Code 宿主面），本课以 Copilot 宿主为例，不展开。

## 11. 真源回链表（按环查）

| 环 | 真源（先读这些） |
| --- | --- |
| 全链主纲 | `TriCompany/docs/workflow/host-object-publish-flow.md` |
| source | `TriCompany/docs/workflow/host-object-publish-flow.md` §3；`TriCompany/runtime/cognition/employee_source_kit.py`；`TriCompany/source-agents/<employee-id>/` 五件套 |
| support | `TriMetaverse/docs/workflow/tricompany-copilot-host-assets-governance.md`；`TriMetaverse/docs/workflow/tricompany-copilot-host-assets-migration-matrix.md`；`TriCompany/runtime/cognition/employee_host_object_generation.py` |
| binding | `TriCompany/.github/binding-profiles/<employee-id>.json`；`TriCompany/runtime/cognition/employee_host_binding_profile_generation.py` |
| live | `TriMetaverse/.github/agents/<employee-id>.agent.md`；`TriCompany/source-agents/registries/trimetaverse-live-agent-publish-manifest.json` |
| manifest | `TriCompany/.github/manifests/tricompany-host-object-generation-manifest.json`；`TriCompany-copilot-host-assets/host-object-manifest.json` |
| governance | `TriCompany/docs/workflow/host-object-publish-flow.md` §2（第 11 步 + 补充治理）；CHO / CAO 治理文件 |
| 规划中 | `TriCompany/docs/engineering/ade-consolidation-proposal.md` v1.0（2026-08-19 CEO 采纳，待分阶段执行） |

## 12. 当前不写成已完成的事项

1. 不写成本课描述的 Copilot-host 六环就是 TriMC 正式宿主切换。
2. 不写成多宿主渲染模型、binding profile 派生化、live entry 渲染化已经实现（见第 10 节，均为规划中）。
3. 不写成 `employee_host_publish` 会自动启用 live agent。
4. 不写成 knowledge 资产已被三端消费（当前处于「只生成、无消费」状态）。
5. 不写成发布链各环节都已进入成熟期免签流程（调试阶段按当前阶段验收记录，成熟后需按授权矩阵签字）。
