# ProvideOptions

ProvideOptions是\@Provide的选项。允许在同一组件树上通过allowOverride重写同名的\@Provide，适用于子组件需要覆盖父组件同名\@Provide值的场景，提高了跨层级状态管理的灵活性。具体例子可见 [\@Provide支持allowOverride参数](../../../ui/state-management/arkts-provide-and-consume.md#provide支持allowoverride参数)。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare interface ProvideOptions--><!--Device-unnamed-declare interface ProvideOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowOverride

```TypeScript
allowOverride?: string
```

允许@Provide重写的别名。允许在同一组件树下通过allowOverride重写同名的@Provide。 缺省时表示@Provide不允许重写。若在未设置allowOverride的情况下定义同名@Provide，运行时会报错。

**类型：** string

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProvideOptions-allowOverride?: string--><!--Device-ProvideOptions-allowOverride?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

