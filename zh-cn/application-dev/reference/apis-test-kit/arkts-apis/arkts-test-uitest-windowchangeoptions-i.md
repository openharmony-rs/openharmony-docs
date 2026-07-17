# WindowChangeOptions

窗口变化事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。

**起始版本：** 22

<!--Device-unnamed-declare interface WindowChangeOptions--><!--Device-unnamed-declare interface WindowChangeOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## bundleName

```TypeScript
bundleName?: string
```

监听窗口对应包名，缺省时默认监听所有窗口。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WindowChangeOptions-bundleName?: string--><!--Device-WindowChangeOptions-bundleName?: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## timeout

```TypeScript
timeout?: number
```

监听超时时间，默认值为10000，单位：ms。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WindowChangeOptions-timeout?: int--><!--Device-WindowChangeOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

