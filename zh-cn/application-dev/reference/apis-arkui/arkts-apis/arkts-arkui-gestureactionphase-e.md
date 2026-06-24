# GestureActionPhase

```TypeScript
export const enum GestureActionPhase
```

这是一个枚举类型，表示要触发的手势回调阶段，对应于 gesture.d.ts 中定义的动作回调。因此，并非所有手势类型都具有以下所有阶段定义。例如，SwipeGesture 只有一个名为 onAction 的回调，因此它也只有一个枚举类型，即 WILL_START。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_START

```TypeScript
WILL_START = 0
```

该手势已被系统成功识别，action-start/action回调函数将立即执行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_END

```TypeScript
WILL_END = 1
```

这表示手势已被确定为结束，这通常发生在用户抬起手指，结束整个交互时，并且动作结束回调将立即执行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

