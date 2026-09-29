# KeyOptions

```TypeScript
declare interface KeyOptions
```

Represents the options for key operations.

**Since:** 26.0.0

<!--Device-unnamed-declare interface KeyOptions--><!--Device-unnamed-declare interface KeyOptions-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## key1

```TypeScript
key1?: number
```

The first keyCode to press during the operation. If not set, no key event will be injected. Setting only key2 without key1 will result in a BusinessError 17000007.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-KeyOptions-key1?: int--><!--Device-KeyOptions-key1?: int-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## key2

```TypeScript
key2?: number
```

The second KeyCode to press during the operation. If not set, no key event will be injected. Setting only key2 without key1 will result in a BusinessError 17000007.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-KeyOptions-key2?: int--><!--Device-KeyOptions-key2?: int-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
