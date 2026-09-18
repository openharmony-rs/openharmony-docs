# InputTextMode

Describes the text input mode.

**Since:** 20

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## addition

```TypeScript
addition?: boolean
```

Whether to input text in addition mode. The value **true** means to input text in addition mode, and **false** means the opposite. Default value: **false**

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## paste

```TypeScript
paste?: boolean
```

Whether to copy and paste text. The value **true** means to copy and paste text, and **false** means to type text. Default value: **false**

**Note:**  If the input text contains Chinese characters, special characters, or the text length exceeds 200 characters, the text is copied and pasted regardless of the value of this parameter.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
