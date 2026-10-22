# PenKeyOperationOptions

```TypeScript
declare interface PenKeyOperationOptions
```

手写笔按键操作选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface PenKeyOperationOptions--><!--Device-unnamed-declare interface PenKeyOperationOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## point

```TypeScript
point?: Point
```

空鼠模式下的坐标点，在[triggerPenKey](arkts-test-uitest-driver-c.md#triggerpenkey)接口中，当参数key设置为[AIR_MOUSE](arkts-test-uitest-penkey-e.md)时必须设置该属性，否则接口调用抛出17000007错误码。

**类型：** [Point](arkts-test-uitest-point-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-PenKeyOperationOptions-point?: Point--><!--Device-PenKeyOperationOptions-point?: Point-End-->

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。
