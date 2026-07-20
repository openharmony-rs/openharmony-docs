# FocusPriority

设置组件焦点的优先级。

**起始版本：** 12

<!--Device-unnamed-declare enum FocusPriority--><!--Device-unnamed-declare enum FocusPriority-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

默认的优先级，缺省时组件的获焦优先级。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusPriority-AUTO = 0--><!--Device-FocusPriority-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PRIOR

```TypeScript
PRIOR = 2000
```

容器内优先获焦的优先级。优先级高于AUTO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusPriority-PRIOR = 2000--><!--Device-FocusPriority-PRIOR = 2000-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREVIOUS

```TypeScript
PREVIOUS = 3000
```

上一次容器整体失焦时获焦节点的优先级。优先级高于PRIOR。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusPriority-PREVIOUS = 3000--><!--Device-FocusPriority-PREVIOUS = 3000-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

