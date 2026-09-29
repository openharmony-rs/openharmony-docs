# Point

```TypeScript
declare interface Point
```

Represents the point on the device screen.

**Since:** 9

<!--Device-unnamed-declare interface Point--><!--Device-unnamed-declare interface Point-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## displayId

```TypeScript
displayId?: number
```

ID of the display to which the coordinate point belongs. The default value is the default screen ID of the device.

**Type:** number

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-Point-displayId?: int--><!--Device-Point-displayId?: int-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## x

```TypeScript
x: number
```

Horizontal coordinate of a coordinate point, in pixels. The value is an integer greater than or equal to 0.

@readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Point-x: int--><!--Device-Point-x: int-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## y

```TypeScript
y: number
```

Vertical coordinate of a coordinate point, in pixels. The value is an integer greater than or equal to 0.

@readonly [since 9-19]

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Point-y: int--><!--Device-Point-y: int-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
