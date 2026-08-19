# inWindow

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## inWindow

```TypeScript
export function inWindow(bundleName: string): On
```

Specifies the bundleName of the application which the window that the target Component is located belongs.

**起始版本：** 23

<!--Device-ON-export function inWindow(bundleName: string): On--><!--Device-ON-export function inWindow(bundleName: string): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | the bundleName of the specified window. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

