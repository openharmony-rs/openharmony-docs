# Rect

Represents the rectangle area on the device screen.

**Since:** 9

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## bottom

```TypeScript
bottom: number
```

Y coordinate of the lower right corner of the component border, in pixels. The value is an integer greater than or equal to 0. @readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## displayId

```TypeScript
displayId?: number
```

ID of the display to which the component border belongs. The value is an integer greater than or equal to 0. <br>Default value: the default screen ID of the device.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## left

```TypeScript
left: number
```

X coordinate of the upper left corner of the component border, in pixels. The value is an integer greater than or equal to 0. @readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## right

```TypeScript
right: number
```

X coordinate of the lower right corner of the component border, in pixels. The value is an integer greater than or equal to 0. @readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## top

```TypeScript
top: number
```

Y coordinate of the upper left corner of the component border, in pixels. The value is an integer greater than or equal to 0. @readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
