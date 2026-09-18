# UIElementInfo

UI事件的相关信息。

**起始版本：** 10

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

应用包名。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## componentEventType

```TypeScript
readonly componentEventType?: ComponentEventType
```

控件操作事件类型，若非控件操作事件返回ComponentEventType.COMPONENT_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [ComponentEventType](arkts-test-uitest-componenteventtype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## componentId

```TypeScript
readonly componentId?: string
```

控件id，若非控件操作事件返回空字符串。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## componentRect

```TypeScript
readonly componentRect?: Rect
```

控件边框信息，若非控件操作事件则返回属性值均为0的Rect对象。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [Rect](arkts-test-uitest-rect-i.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## text

```TypeScript
readonly text: string
```

控件/窗口的文本信息。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## type

```TypeScript
readonly type: string
```

控件/窗口类型。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## windowChangeType

```TypeScript
readonly windowChangeType?: WindowChangeType
```

窗口变化事件类型，若非窗口变化事件返回WindowChangeType.WINDOW_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [WindowChangeType](arkts-test-uitest-windowchangetype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## windowId

```TypeScript
readonly windowId?: number
```

控件所属窗口id。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。
