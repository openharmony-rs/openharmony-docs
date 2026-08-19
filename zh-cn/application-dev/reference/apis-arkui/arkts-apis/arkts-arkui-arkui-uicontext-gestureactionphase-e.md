# GestureActionPhase

此枚举类型表示手势回调触发阶段，对应gesture.d.ts中定义的动作回调，但不同手势类型支持的阶段不同（如SwipeGesture仅包含WILL_START枚举值）。

**起始版本：** 20

<!--Device-unnamed-export const enum GestureActionPhase--><!--Device-unnamed-export const enum GestureActionPhase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_START

```TypeScript
WILL_START = 0
```

该手势已被系统成功识别，action-start/action回调函数将立即执行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GestureActionPhase-WILL_START = 0--><!--Device-GestureActionPhase-WILL_START = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_END

```TypeScript
WILL_END = 1
```

这表示手势已被确定为结束，这通常发生在用户抬起手指，结束整个交互时，并且动作结束回调将立即执行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GestureActionPhase-WILL_END = 1--><!--Device-GestureActionPhase-WILL_END = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

