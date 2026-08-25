# TriTraining Product State

> Owner：ChiefProductOfficer（CPO，小乔）
> 日期：2026-07-17
> 状态：产品定位完成（CEO 确认 Phase 1 L3），待 CTO 执行建仓

## 文档同步元信息

- sourceOfTruth: TriTraining/docs/registry/product-state.md
- publishedFrom: 当前文件（source）
- syncMode: source-only
- publishTier: source-only
- lastSyncedAt: 2026-07-17T03:35:00+08:00

---

## 模块定位

TriTraining 是三元宇宙的**免费 AI 培训获客产品**，面向外部零基础用户，通过短课程路径引导用户完成"AI 扫盲 → TriMetaverse 上手 → 首次对话 → 获得奖励 → 晋级社区成员"的获客漏斗。

## 双轨拆分

TriTraining 仓内存在两轨内容，归属不同 owner：

| 轨 | 内容 | Owner | 状态 |
|---|---|---|---|
| **获客轨（产品）** | 面向外部用户的 AI 扫盲 + TriMetaverse 入门课程 | CPO（小乔） | 产品定位完成，待 Phase 1 L3 启动 |
| **内训轨（支撑）** | 面向内部员工的入职培训（source-kit-cli、host-publish-pipeline 等） | RAndDTrainer（小吴）+ CTO（小狄） | 已有 16 份文档，继续维护 |

CPO 只对获客轨承担产品 owner 责任。内训轨不在 TriTraining 产品范围内。

---

## MVP 定义（获客轨）

```
TriTraining MVP = 一条"AI 扫盲 → TriMetaverse 上手"的免费课程路径

课程结构：
  L1: 什么是 AI Agent？（零基础，~5 分钟）
  L2: TriMetaverse 能帮你做什么？（3 个场景 demo）
  L3: 注册 → 首次对话 → 获得第一个奖励（引导完成首次 TriPilot 对话）

产品边界：
  ✅ 短课程路径（3 课）
  ✅ TriAvatar 前端渲染课程页
  ✅ TriStaciss 后端记录完成状态 + 发放奖励
  ✅ 培训完成 → 自动晋级"社区成员"
  ❌ LMS（学习管理系统）
  ❌ 考试/证书系统
  ❌ 付费课程
  ❌ 社区论坛/UGC
  ❌ 多语言（Phase 1 仅中文）
```

## Phase 归属

- **Phase 1 L3（获客层）**
- 启动条件：L0（核心产品）+ L1（PC 端入口）+ L2（社交获客）落稳后
- 当前阶段：只做产品定位 + registry 初始化，**不建代码、不开工**

## 协作模块

| 模块 | 角色 | 就绪度 |
|---|---|---|
| TriAvatar | 前端渲染课程页、lesson page | DISCOVERY，Phase 1 L1 静态头像先行 |
| TriStaciss | 后端记录完成状态、发放平台奖励 | CTO-004 APPROVED，coding 中 |
| TriMC | 用户身份 + 晋级状态 | Phase 1+2 done |
| TriMem | 统一用户身份中枢 | Phase 1 L0 done，L1 W30 |

## 用户晋级链路

```
外部访客
  → 浏览 TriTraining 课程（无需登录）
  → 注册 TriMetaverse 账号
  → 完成 L3 引导（首次对话）
  → TriStaciss 发放首次平台奖励
  → 自动晋级"社区成员"
  → 进入获客漏斗下一环（TriMobile/TriGateway）
```

晋级规则对齐 CPO 前序裁决：注册用户 → 社区成员 = 自动触发，条件为首次收到平台奖励（含完成培训奖励）。

## 当前状态

- [x] 模块仓已存在（`D:\OneDrive\Code\ai\TriTraining`）
- [x] 产品定位完成（CPO，2026-07-17）
- [x] Phase 归属确认（CEO 批准 Phase 1 L3，2026-07-17）
- [ ] TriTraining/docs/registry/product-state.md 初始化（本文档）
- [ ] CTO 确认工程边界（获客轨/内训轨目录分离）
- [ ] CTO 执行 CEO-005 建仓（完善目录结构、CI/CD 等）
- [ ] 课程内容制作（Phase 1 L3 启动前另排）

## 风险

- 获客轨与内训轨在同一仓库，物理边界需 CTO 明确（建议 `docs/product/` = 获客，`docs/training/` = 内训）
- TriAvatar 课程页渲染能力待验证，可能成为 Phase 1 L3 启动的阻塞项
- 若 CEO 要求当前阶段即开工（而非仅定位），需重新评估 TriAvatar/TriStaciss 就绪度

## 使用依据

- CEO-005 note（OP-202607-W29-001）：「免费零基础 AI 培训获客，归入研发质量层 L3」
- CEO 2026-07-17 确认：Phase 2+ → Phase 1 L3
- CPO 前序裁决：用户晋级链路 + TriAvatar/TriStaciss 协作接口
- TriCompany product-state.md §Simplest Verifiable Model + §Product Role Matrix
- TriTraining/AGENTS.md + README.md + docs/training/README.md
