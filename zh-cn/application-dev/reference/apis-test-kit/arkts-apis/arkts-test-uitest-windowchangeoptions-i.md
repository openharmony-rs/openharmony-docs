# WindowChangeOptions

窗口变化事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。

**起始版本：** 23

<!--Device-unnamed-declare interface WindowChangeOptions--><!--Device-unnamed-declare interface WindowChangeOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## bundleName

```TypeScript
bundleName?: string
```

监听窗口对应包名，缺省时默认监听所有窗口。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowChangeOptions-bundleName?: string--><!--Device-WindowChangeOptions-bundleName?: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## timeout

```TypeScript
timeout?: int
```

监听超时时间，取值范围：大于等于500的整数，默认值为10000，单位：ms。传入不在范围内的值抛出错误码。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowChangeOptions-timeout?: int--><!--Device-WindowChangeOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

