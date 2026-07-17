# DragEventParam

拖拽结束返回结果的回调。

**起始版本：** 12

<!--Device-dragController-interface DragEventParam--><!--Device-dragController-interface DragEventParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## event

```TypeScript
event: DragEvent
```

拖拽事件信息，仅包括拖拽结果。

**类型：** DragEvent

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragEventParam-event: DragEvent--><!--Device-DragEventParam-event: DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams: string
```

设置拖拽事件额外信息，具体功能暂未实现。

默认值：空

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragEventParam-extraParams: string--><!--Device-DragEventParam-extraParams: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

