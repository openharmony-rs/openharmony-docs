# InputTextMode

输入文本的方式。

**起始版本：** 20

<!--Device-unnamed-declare interface InputTextMode--><!--Device-unnamed-declare interface InputTextMode-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## addition

```TypeScript
addition?: boolean
```

输入文本时是否以追加的方式进行输入。true：以追加方式输入。false：不以追加方式输入。默认为false。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-InputTextMode-addition?: boolean--><!--Device-InputTextMode-addition?: boolean-End-->

**系统能力：** SystemCapability.Test.UiTest

## paste

```TypeScript
paste?: boolean
```

输入文本时是否指定以复制粘贴方式输入。true：指定以复制粘贴方式输入。false：指定以逐字键入方式输入。默认为false。

**说明：** 当输入文本中包含中文、特殊字符或文本长度超过200字符时，无论该参数取值为何，均以复制粘贴方式输入。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-InputTextMode-paste?: boolean--><!--Device-InputTextMode-paste?: boolean-End-->

**系统能力：** SystemCapability.Test.UiTest

