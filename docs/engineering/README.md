# TriTraining Engineering

> Owner：ChiefTechnologyOfficer（小狄）
> 日期：2026-07-17
> 状态：工程边界确认完成，Phase 1 L3 启动前不开工

## 工程边界：获客轨 / 内训轨双轨分离

CTO 确认以下物理边界，对齐 CPO 产品定位（`docs/registry/product-state.md`）：

| 目录 | 轨 | Owner | 内容 |
|---|---|---|---|
| `docs/product/` | **获客轨**（产品） | CPO（小乔） | 面向外部用户的 AI 扫盲 + TriMetaverse 入门课程内容 |
| `docs/training/` | **内训轨**（支撑） | RAndDTrainer（小吴）+ CTO（小狄） | 面向内部员工的入职培训文档（已有 16 份） |

**纪律**：
- 获客轨课程内容（lesson contract、lab contract、课程图谱等）写入 `docs/product/`，由 CPO 管理产品边界
- 内训轨培训文档写入 `docs/training/`，由 RAndDTrainer/CTO 维护
- 两轨不混写；交叉引用需显式标注来源轨
- 代码实现（如有）统一放在仓根 `src/` 下，不按轨拆分代码目录

## 模块工程骨架

当前已具备：
- [x] 独立 Git 仓库
- [x] `README.md`
- [x] `AGENTS.md`
- [x] `docs/` 六件套（product / engineering / training / registry / execution / workflow）
- [ ] `.gitignore`（待 CTO 补齐）
- [ ] 本地 CodeGraph 初始化（待 CTO 执行）
- [ ] CI/CD 配置（待 Phase 1 L3 启动前补齐）

## Phase 1 L3 启动前置条件

- L0（核心产品）+ L1（PC 端入口）+ L2（社交获客）落稳
- TriAvatar 课程页渲染能力就绪
- TriStaciss 完成状态记录 + 奖励发放接口
- 以上条件满足前，TriTraining 工程侧只做骨架维护，不开工写业务代码
