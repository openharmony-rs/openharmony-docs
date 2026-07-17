# ScrollEventInfo

ScrollEvent info.

**起始版本：** 12

<!--Device-uiObserver-export interface ScrollEventInfo--><!--Device-uiObserver-export interface ScrollEventInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## axis

```TypeScript
axis?: Axis
```

滚动方向。

**类型：** Axis

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEventInfo-axis?: Axis--><!--Device-ScrollEventInfo-axis?: Axis-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string
```

Scroll id.

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEventInfo-id: string--><!--Device-ScrollEventInfo-id: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

Changed ScrollEvent offset.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEventInfo-offset: number--><!--Device-ScrollEventInfo-offset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollEvent

```TypeScript
scrollEvent: ScrollEventType
```

Changed ScrollEvent type.

**类型：** ScrollEventType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEventInfo-scrollEvent: ScrollEventType--><!--Device-ScrollEventInfo-scrollEvent: ScrollEventType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId: number
```

The uniqueId of the scrollable component.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEventInfo-uniqueId: number--><!--Device-ScrollEventInfo-uniqueId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

