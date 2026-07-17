# ComponentEventOptions

控件操作事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。

**起始版本：** 22

<!--Device-unnamed-declare interface ComponentEventOptions--><!--Device-unnamed-declare interface ComponentEventOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## on

```TypeScript
on?: On
```

监听目标控件的属性要求，默认监听所有控件。

**说明：** 仅支持监听指定属性要求的控件，不支持监听指定On.isBefore、On.isAfter、On.within等相对位置的控件。

**类型：** On

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentEventOptions-on?: On--><!--Device-ComponentEventOptions-on?: On-End-->

**系统能力：** SystemCapability.Test.UiTest

## timeout

```TypeScript
timeout?: number
```

监听超时时间，默认值为10000，单位：ms。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentEventOptions-timeout?: int--><!--Device-ComponentEventOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

