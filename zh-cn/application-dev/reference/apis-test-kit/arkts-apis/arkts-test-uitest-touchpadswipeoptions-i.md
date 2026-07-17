# TouchPadSwipeOptions

触摸板多指滑动手势选项相关信息。

**起始版本：** 18

<!--Device-unnamed-declare interface TouchPadSwipeOptions--><!--Device-unnamed-declare interface TouchPadSwipeOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## speed

```TypeScript
speed?: number
```

滑动速率，取值范围为200-40000的整数，默认值为2000，单位：px/s。为不在范围内的非负数或为null/undefined时设为默认值2000。为负数时抛出参数错误的错误码。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TouchPadSwipeOptions-speed?: int--><!--Device-TouchPadSwipeOptions-speed?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## stay

```TypeScript
stay?: boolean
```

触摸板多指滑动结束是否停留1s后再抬起，默认为false（不停留1s），true：停留，false：不停留。

**类型：** boolean

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TouchPadSwipeOptions-stay?: boolean--><!--Device-TouchPadSwipeOptions-stay?: boolean-End-->

**系统能力：** SystemCapability.Test.UiTest

