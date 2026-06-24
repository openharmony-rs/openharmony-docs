# DragSpringLoadingState

```TypeScript
const enum DragSpringLoadingState
```

定义拖拽的悬停检测状态的枚举类型。
默认系统配置下，如果没有触发CANCEL，状态报告如下：
保持Hover-->500ms-->BEGIN-->100ms-->UPDATE-->100ms-->UPDATE-->100ms-->UPDATE-->100ms-->END

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BEGIN

```TypeScript
BEGIN = 0
```

拖拽进入组件范围静止一段时间，被识别为悬停状态。此时允许进行一些悬停检测的准备操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UPDATE

```TypeScript
UPDATE = 1
```

Already in the spring loading state. The system periodically checks the user's hover status.
If the user remains stationary, it triggers an UPDATE state notification at regular intervals.
This state allows for UI effect refreshes to emphasize the hover state.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 2
```

The entire spring loading state ends. The application can perform cleanup operations
and execute navigation or view switching actions when this state occurs.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL = 3
```

After entering the BEGIN state, if the user moves out of the component range, exceeds the displacement
threshold, lifts the finger, or switches windows (pull out), the CANCEL state is triggered.
The application should restore the UI style and cancel any pending navigation or view switching actions.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

