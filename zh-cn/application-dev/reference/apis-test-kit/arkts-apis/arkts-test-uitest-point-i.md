# Point

坐标点信息。

**起始版本：** 9

<!--Device-unnamed-declare interface Point--><!--Device-unnamed-declare interface Point-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## displayId

```TypeScript
displayId?: number
```

坐标点所属的屏幕ID，取值范围：大于等于0的整数。默认值为设备默认屏幕ID。

从API version 20开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Point-displayId?: int--><!--Device-Point-displayId?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## x

```TypeScript
x: number
```

坐标点的横坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Point-x: int--><!--Device-Point-x: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## y

```TypeScript
y: number
```

坐标点的纵坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Point-y: int--><!--Device-Point-y: int-End-->

**系统能力：** SystemCapability.Test.UiTest

