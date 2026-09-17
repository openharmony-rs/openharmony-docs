# UIElementInfo

Provides information about the UI event.

**Since:** 10

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## componentEventType

```TypeScript
readonly componentEventType?: ComponentEventType
```

Component operation event type. If it is not a component operation event, [COMPONENT_UNDEFINED](arkts-test-uitest-componenteventtype-e.md#component_undefined) is returned.

**Type:** [ComponentEventType](arkts-test-uitest-componenteventtype-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## componentId

```TypeScript
readonly componentId?: string
```

Component ID. If it is not a component operation event, an empty string is returned.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## componentRect

```TypeScript
readonly componentRect?: Rect
```

Component border information. If it is not a component operation event, a [Rect](arkts-test-uitest-rect-i.md) object whose attribute values are all **0** is returned.

**Type:** [Rect](arkts-test-uitest-rect-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## text

```TypeScript
readonly text: string
```

Text information of the component or window.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## type

```TypeScript
readonly type: string
```

Component or window type.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## windowChangeType

```TypeScript
readonly windowChangeType?: WindowChangeType
```

Window change event type. If the event is not a window change event, [WINDOW_UNDEFINED](arkts-test-uitest-windowchangetype-e.md#window_undefined) is returned.

**Type:** [WindowChangeType](arkts-test-uitest-windowchangetype-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## windowId

```TypeScript
readonly windowId?: number
```

ID of the window to which the component belongs. If it is not a component operation event, **-1** is returned.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
