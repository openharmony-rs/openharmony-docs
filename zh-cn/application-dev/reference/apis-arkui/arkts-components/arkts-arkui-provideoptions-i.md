# ProvideOptions

Defines the options of Provide PropertyDecorator.

**起始版本：** 11

<!--Device-unnamed-declare interface ProvideOptions--><!--Device-unnamed-declare interface ProvideOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowOverride

```TypeScript
allowOverride?: string
```

Override the @Provide of any parent or parent of parent @Component.@Provide({allowOverride: "name"}) is also allowed to be used even when there is no ancestor @Component whose @Provide would be overridden.

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProvideOptions-allowOverride?: string--><!--Device-ProvideOptions-allowOverride?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

