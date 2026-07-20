# KeyProcessingMode

设置按键事件处理的优先级。

**起始版本：** 15

<!--Device-unnamed-declare enum KeyProcessingMode--><!--Device-unnamed-declare enum KeyProcessingMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOCUS_NAVIGATION

```TypeScript
FOCUS_NAVIGATION = 0
```

默认值，当前组件不消费按键时，tab/方向键优先在当前容器内走焦。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-KeyProcessingMode-FOCUS_NAVIGATION = 0--><!--Device-KeyProcessingMode-FOCUS_NAVIGATION = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ANCESTOR_EVENT

```TypeScript
ANCESTOR_EVENT = 1
```

当前组件不消费按键时，tab/方向键优先冒泡给父组件。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-KeyProcessingMode-ANCESTOR_EVENT = 1--><!--Device-KeyProcessingMode-ANCESTOR_EVENT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

