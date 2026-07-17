# PenKeyOperationOptions

笔按键操作选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface PenKeyOperationOptions--><!--Device-unnamed-declare interface PenKeyOperationOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## point

```TypeScript
point?: Point
```

空鼠模式操作的坐标点。当按键为 AIR_MOUSE 并处于空鼠模式时，该坐标点是必需的。

**类型：** Point

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PenKeyOperationOptions-point?: Point--><!--Device-PenKeyOperationOptions-point?: Point-End-->

**系统能力：** SystemCapability.Test.UiTest

