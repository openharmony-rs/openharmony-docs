# hint

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## hint

```TypeScript
export function hint(val: string, pattern?: MatchPattern): On
```

Specifies the hint for the target Component.

**起始版本：** 23

<!--Device-ON-export function hint(val: string, pattern?: MatchPattern): On--><!--Device-ON-export function hint(val: string, pattern?: MatchPattern): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | string | 是 | the hint value. |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | the [MatchPattern](arkts-test-uitest-matchpattern-e.md) of the text value,Set it default [EQUALS](arkts-test-uitest-matchpattern-e.md#equals) if null or undefined. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

