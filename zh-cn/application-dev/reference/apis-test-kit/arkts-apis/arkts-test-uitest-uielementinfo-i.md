# UIElementInfo

UI事件的相关信息。

**起始版本：** 10

<!--Device-unnamed-declare interface UIElementInfo--><!--Device-unnamed-declare interface UIElementInfo-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

应用包名。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly bundleName: string--><!--Device-UIElementInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## componentEventType

```TypeScript
readonly componentEventType?: ComponentEventType
```

控件操作事件类型，若非控件操作事件返回ComponentEventType.COMPONENT_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** ComponentEventType

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly componentEventType?: ComponentEventType--><!--Device-UIElementInfo-readonly componentEventType?: ComponentEventType-End-->

**系统能力：** SystemCapability.Test.UiTest

## componentId

```TypeScript
readonly componentId?: string
```

控件id，若非控件操作事件返回空字符串。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly componentId?: string--><!--Device-UIElementInfo-readonly componentId?: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## componentRect

```TypeScript
readonly componentRect?: Rect
```

控件边框信息，若非控件操作事件则返回属性值均为0的Rect对象。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** Rect

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly componentRect?: Rect--><!--Device-UIElementInfo-readonly componentRect?: Rect-End-->

**系统能力：** SystemCapability.Test.UiTest

## text

```TypeScript
readonly text: string
```

控件/窗口的文本信息。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly text: string--><!--Device-UIElementInfo-readonly text: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## type

```TypeScript
readonly type: string
```

控件/窗口类型。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly type: string--><!--Device-UIElementInfo-readonly type: string-End-->

**系统能力：** SystemCapability.Test.UiTest

## windowChangeType

```TypeScript
readonly windowChangeType?: WindowChangeType
```

窗口变化事件类型，若非窗口变化事件返回WindowChangeType.WINDOW_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** WindowChangeType

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly windowChangeType?: WindowChangeType--><!--Device-UIElementInfo-readonly windowChangeType?: WindowChangeType-End-->

**系统能力：** SystemCapability.Test.UiTest

## windowId

```TypeScript
readonly windowId?: number
```

控件所属窗口id。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIElementInfo-readonly windowId?: int--><!--Device-UIElementInfo-readonly windowId?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

