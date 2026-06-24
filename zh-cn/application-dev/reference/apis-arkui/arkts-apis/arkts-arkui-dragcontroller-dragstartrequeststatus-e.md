# DragStartRequestStatus

```TypeScript
const enum DragStartRequestStatus
```

定义应用是否可以发起拖拽的枚举类型。仅在[onDragStart](arkts-arkui-commonmethod-c.md#onDragStart-1)调用时有效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WAITING

```TypeScript
WAITING = 0
```

应用在准备数据阶段，无法发起拖拽。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## READY

```TypeScript
READY = 1
```

应用数据准备完成，可以发起拖拽。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

