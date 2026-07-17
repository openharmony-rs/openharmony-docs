# Rect

控件的边框信息。

**起始版本：** 9

<!--Device-unnamed-declare interface Rect--><!--Device-unnamed-declare interface Rect-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## bottom

```TypeScript
bottom: number
```

控件边框的右下角的Y坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-bottom: int--><!--Device-Rect-bottom: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## displayId

```TypeScript
displayId?: number
```

控件边框所属的屏幕ID，取值大于或等于0的整数。默认值为设备默认屏幕ID。

从API version 20开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-displayId?: int--><!--Device-Rect-displayId?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## left

```TypeScript
left: number
```

控件边框的左上角的X坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-left: int--><!--Device-Rect-left: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## right

```TypeScript
right: number
```

控件边框的右下角的X坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-right: int--><!--Device-Rect-right: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## top

```TypeScript
top: number
```

控件边框的左上角的Y坐标，取值大于0的整数。

**说明：** 从API version 20开始，该属性不再为只读属性。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-top: int--><!--Device-Rect-top: int-End-->

**系统能力：** SystemCapability.Test.UiTest

