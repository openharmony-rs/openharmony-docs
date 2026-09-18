# TouchOptions

Common options for touch operations.

**Since:** 26.0.0

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## duration

```TypeScript
duration?: number
```

Duration of the operation in milliseconds. <br>Value range: The value should be &gt;= 1500 <br>Unit: ms <br>Default value: 1500

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## pressure

```TypeScript
pressure?: number
```

Pressure value of the touch. The value range is [0, 1]. The default value is **0**. If the value is **null** or **undefined**, the default value is used. If the value is out of the value range, the 17000007 error code is thrown.

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## speed

```TypeScript
speed?: number
```

Speed of touch action. <br>Value range:[200, 40000] <br>Unit: px/s. <br>If the value is out of range or null/undefined, the default value 600 is used. <br>Default value: 600

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
