# WindowFilter

Provides the flag attributes of this window.

**Since:** 9

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## active

```TypeScript
active?: boolean
```

Whether the window is interacting with the user. The value **true** indicates that the window is interacting with the user, and **false** indicates the opposite.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## actived

```TypeScript
actived?: boolean
```

Whether the window is interacting with the user. The value **true** indicates that the window is interacting with the user, and **false** indicates the opposite.

This API is supported since API version 9 and deprecated since API version 11. You are advised to use [active](#active) instead.

**Type:** boolean

**Since:** 9

**Deprecated since:** 11

**Substitutes:** active

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the application to which the window belongs, which is used to filter the target window in multi-window scenarios. This parameter is left empty by default.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## displayId

```TypeScript
displayId?: number
```

ID of the display to which the window belongs. The default value is the default screen ID of the device.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## focused

```TypeScript
focused?: boolean
```

Whether the window is focused. The value **true** indicates that the window is focused, and **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## title

```TypeScript
title?: string
```

Window title, which is used to filter the target window in multi-window scenarios. This parameter is left empty by default.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
