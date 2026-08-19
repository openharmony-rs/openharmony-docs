# enabled

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## enabled

```TypeScript
export function enabled(b?: boolean): On
```

Specifies the enabled status of the target Component.

**起始版本：** 23

<!--Device-ON-export function enabled(b?: boolean): On--><!--Device-ON-export function enabled(b?: boolean): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | the enabled status.Set it default true if null or undefined. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

