# TriTraining Agent Rules

## Module Role

- TriTraining 是培训学院功能主承载模块。
- 它负责课程组织、lesson / lab contract、课程图谱、训练运行规则，以及与 `TriAvatar` / `TriStaciss` 的协作接口。
- 当商业模式涉及培训学院、课程体系、训练发布和学习路径承接时，需要考虑本模块。

## Current Status

- 当前仓库处于最小模块基线初始化阶段。
- 当前只完成模块骨架与 training 真源入口初始化。
- 培训学院产品边界、技术边界和宿主发布链仍需 `CPO` / `CTO` 联审收口。
- 在真实实现、扩展 README、registry 或模块 agent 落地前，不要把培训学院整体写成已完成平台。

## Strategy Delegation

- 总商业模式、模块优先级、`TriTraining` 与其他模块的边界变化，先咨询 `TriMetaverse/BusinessStrategy`。
- 不要把 `TriTraining` 与 `TriAvatar`、`TriStaciss` 的协作面写成替代关系。

## Local Fact Sources

- 产品事实优先看：`README.md`、`docs/product/`
- 技术事实优先看：`docs/engineering/` 与未来真实实现目录
- training 真源优先看：`docs/training/`

## Update Discipline

- 明确区分“模块 training 真源”“中央 training 聚合包”“宿主侧 published copy”。
- 禁止把 `TriMetaverse/docs/training/tritraining/` 或 `TriTraining-copilot-host-assets` 写成模块真源。
- 资料不足时标为 `待初始化`、`待确认` 或 `待联审`。
