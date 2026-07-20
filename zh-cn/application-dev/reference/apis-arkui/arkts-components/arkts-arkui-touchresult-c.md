# TouchResult

自定义事件分发结果，开发者通过返回结果来影响事件分发。

**起始版本：** 11

<!--Device-unnamed-declare class TouchResult--><!--Device-unnamed-declare class TouchResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

子组件的唯一标识。

当strategy为TouchTestStrategy.DEFAULT时，id是可选的；当strategy是TouchTestStrategy.FORWARD_COMPETITION或TouchTestStrategy.FORWARD时，id是必需的（如果没有返回id，则当成TouchTestStrategy.DEFAULT处理）。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TouchResult-id?: string--><!--Device-TouchResult-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strategy

```TypeScript
strategy: TouchTestStrategy
```

事件派发策略。

**类型：** TouchTestStrategy

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TouchResult-strategy: TouchTestStrategy--><!--Device-TouchResult-strategy: TouchTestStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

