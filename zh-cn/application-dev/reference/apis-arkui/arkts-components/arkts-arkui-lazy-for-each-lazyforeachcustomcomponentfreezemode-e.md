# LazyForEachCustomComponentFreezeMode

冻结模式枚举，用于配置LazyForEach中已移出组件树的缓存自定义节点的冻结行为。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum LazyForEachCustomComponentFreezeMode--><!--Device-unnamed-declare enum LazyForEachCustomComponentFreezeMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

遵循Metadata中enableCustomComponentFreeze字段的配置来决定是否启用冻结。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachCustomComponentFreezeMode-AUTO = 0--><!--Device-LazyForEachCustomComponentFreezeMode-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

禁用已移出组件树的缓存自定义节点的冻结。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachCustomComponentFreezeMode-DISABLED = 1--><!--Device-LazyForEachCustomComponentFreezeMode-DISABLED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLED

```TypeScript
ENABLED = 2
```

启用已移出组件树的缓存自定义节点的冻结。开启后，缓存自定义组件的状态更新将被冻结。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachCustomComponentFreezeMode-ENABLED = 2--><!--Device-LazyForEachCustomComponentFreezeMode-ENABLED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

