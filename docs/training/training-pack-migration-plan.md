# TriTraining 课程包迁移计划

版本：V0.1
日期：2026-06-14
状态：迁移已完成当前计划批次

## 0. 当前进度

- 已完成课程正文首批迁移：`employee-source-kit-cli-course.md`、`employee-host-publish-pipeline-course.md`
- 已完成第二批迁移：lesson contract、lab contract、lab manual
- 已完成第三批迁移：课程图谱、课程体系架构、样板 JSON

## 1. 目标

把当前中央聚合面中的 `TriMetaverse/docs/training/tritraining/` 课程资产，逐步迁回 `TriTraining/docs/training/`，使 `TriTraining` 模块拥有自己的 training 真源。

## 2. 迁移原则

1. 模块 training 真源优先进入 `TriTraining/docs/training/`。
2. 中央 `TriMetaverse/docs/training/tritraining/` 只保留模块 training 包入口与已发布聚合内容。
3. 宿主侧如需 published copy，按真源发布链进入 `TriTraining-copilot-host-assets`。
4. 每迁移一批内容，就同步修正 `publishedFrom`、`sourceOfTruth` 和中央入口说明。

## 3. 建议迁移批次

1. 顶层索引与定位文档：`README.md`、课程图谱、课程体系架构。
2. 正式课程正文：`employee-source-kit-cli-course.md`、`employee-host-publish-pipeline-course.md`。当前已完成。
3. contract 与实验手册：lesson / lab contract、lab manual。当前已完成。
4. 样板 JSON：`TriAvatar` lesson page、`TriStaciss` lab submission 样板。当前已完成。

## 4. 完成条件

当前三批迁移计划已经完成。下一步若继续，应转入：

1. 修正中央聚合包中各副本的 `sourceOfTruth` / `publishedFrom` 回链。
2. 由 `CPO` / `CTO` 评估后决定，是否需要为宿主侧生成 `TriTraining-copilot-host-assets/docs/training/` published copy。
3. 由 `CPO` / `CTO` 评估后决定，中央聚合包是否继续保留详细正文，还是只保留模块 training 包入口。
