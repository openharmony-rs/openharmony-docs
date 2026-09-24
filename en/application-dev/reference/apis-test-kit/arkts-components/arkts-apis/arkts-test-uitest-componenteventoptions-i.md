# ComponentEventOptions

```TypeScript
declare interface ComponentEventOptions
```

Describes the extended configuration of component operation event listening, which is used to specify the listening process configuration and event filtering conditions.

**Since:** 22

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## on

```TypeScript
on?: On
```

Attribute requirements of the target component to listen for. By default, all components are listened for. **Note:**  Only components with specified attributes can be listened for. Components with relative positions such as **On.isBefore**, **On.isAfter**, and **On.within** cannot be listened for.

**Type:** [On](arkts-test-uitest-on-c.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## timeout

```TypeScript
timeout?: number
```

Listening timeout interval, in milliseconds. The value is an integer greater than or equal to 500. The default value is **10000**. If the value is out of range, an error code is thrown.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
