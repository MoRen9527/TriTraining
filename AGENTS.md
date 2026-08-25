# TriTraining Agent Rules

## Module Role

- TriTraining 是培训学院功能主承载模块。
- 它负责课程组织、lesson / lab contract、课程图谱、训练运行规则，以及与 `TriAvatar` / `TriStaciss` 的协作接口。
- 当商业模式涉及培训学院、课程体系、训练发布和学习路径承接时，需要考虑本模块。

## Current Status

- 2026-07-17：CPO 产品定位完成（获客轨 MVP 3 课路径 + 内训轨归属 RAndDTrainer/CTO），CEO 确认 Phase 1 L3
- 2026-07-17：CTO 工程边界确认（获客轨 `docs/product/` ↔ 内训轨 `docs/training/`），`.gitignore` 已补齐
- Phase 1 L3 启动条件：L0-L2 落稳后方可开工；当前只做定位 + 骨架维护，不开工写业务代码
- 产品真源：`docs/registry/product-state.md`（CPO 维护）
- 工程真源：`docs/engineering/README.md`（CTO 维护）

## Strategy Delegation

- 总商业模式、模块优先级、`TriTraining` 与其他模块的边界变化，先咨询 `TriMetaverse/BusinessStrategy`。
- 不要把 `TriTraining` 与 `TriAvatar`、`TriStaciss` 的协作面写成替代关系。

## Local Fact Sources

- 产品事实优先看：`README.md`、`docs/product/`
- 技术事实优先看：`docs/engineering/` 与未来真实实现目录
- training 真源优先看：`docs/training/`

## Update Discipline

- 明确区分"获客轨"（`docs/product/`，CPO 域）与"内训轨"（`docs/training/`，RAndDTrainer/CTO 域），两轨不混写。
- 明确区分"模块 training 真源""中央 training 聚合包""宿主侧 published copy"。
- 禁止把 `TriMetaverse/docs/training/tritraining/` 或 `TriTraining-copilot-host-assets` 写成模块真源。
- 资料不足时标为 `待初始化`、`待确认` 或 `待联审`。
