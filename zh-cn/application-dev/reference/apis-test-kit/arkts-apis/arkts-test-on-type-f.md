# type

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## type

```TypeScript
export function type(tp: string): On
```

Specifies the type of the target Component.

**起始版本：** 23

<!--Device-ON-export function type(tp: string): On--><!--Device-ON-export function type(tp: string): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | The type value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |


## type

```TypeScript
export function type(tp: string, pattern: MatchPattern): On
```

Specifies the type of the target Component.

**起始版本：** 23

<!--Device-ON-export function type(tp: string, pattern: MatchPattern): On--><!--Device-ON-export function type(tp: string, pattern: MatchPattern): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | The type value. |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 是 | the [MatchPattern](arkts-test-uitest-matchpattern-e.md) of the text value,Set it default [EQUALS](arkts-test-uitest-matchpattern-e.md#equals) if null or undefined. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

