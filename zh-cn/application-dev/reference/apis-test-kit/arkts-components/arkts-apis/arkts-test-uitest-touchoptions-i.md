# TouchOptions

触摸操作的通用选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## duration

```TypeScript
duration?: number
```

操作持续的时间，取值范围为大于等于1500的整数，默认值为1500，单位：ms。取值小于1500时抛出17000007错误码，为null或undefined时使用默认值。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## pressure

```TypeScript
pressure?: number
```

触摸的压力值，取值范围为[0, 1]，包含0和1，默认值为0。取值为null或undefined时按照默认值处理，其他超出取值范围情况时抛出17000007错误码。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## speed

```TypeScript
speed?: number
```

操作速度（每秒像素数），取值范围为 200 到 40000。如果超出范围或为 null 或未定义，则默认设置为 600。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。
