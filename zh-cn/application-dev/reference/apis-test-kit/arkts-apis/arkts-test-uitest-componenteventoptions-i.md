# ComponentEventOptions

控件操作事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。

**起始版本：** 23

<!--Device-unnamed-declare interface ComponentEventOptions--><!--Device-unnamed-declare interface ComponentEventOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## on

```TypeScript
on?: On
```

监听目标控件的属性要求，默认监听所有控件。 **说明：** 仅支持监听指定属性要求的控件，不支持监听指定On.isBefore、On.isAfter、On.within等相对位置的控件。

**类型：** [On](arkts-test-uitest-on-c.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentEventOptions-on?: On--><!--Device-ComponentEventOptions-on?: On-End-->

**系统能力：** SystemCapability.Test.UiTest

## timeout

```TypeScript
timeout?: int
```

监听超时时间，取值范围：大于等于500的整数，默认值为10000，单位：ms。传入不在范围内的值抛出错误码。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentEventOptions-timeout?: int--><!--Device-ComponentEventOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

