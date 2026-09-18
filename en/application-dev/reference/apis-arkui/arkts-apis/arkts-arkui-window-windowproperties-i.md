# WindowProperties

Describes the window properties.

**Since:** 6

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## brightness

```TypeScript
brightness: number
```

Screen brightness of the window. The brightness can be set by calling [setWindowBrightness()](arkts-arkui-window-window-i.md#setwindowbrightness). The value is a floating-point number. Valid values are in the range [0.0, 1.0] (where **1.0** means the brightest) or the special value **-1.0** (which means that the brightness follows the system). If no value is passed, the brightness follows the system. In this case, the obtained brightness value is **-1.0**.

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## dimBehindValue

```TypeScript
dimBehindValue: number
```

Dimness of the window that is not on top. The value is a floating-point number in the range [0.0, 1.0], and the value **1.0** means the dimmest.

Note: This property is supported since API version 7 and deprecated since API version 9. Currently, no substitute is available.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## displayId

```TypeScript
displayId?: number
```

ID of the screen where the window is located. By default, the ID of the main screen is returned. The value is an integer.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## drawableRect

```TypeScript
drawableRect: Rect
```

Size of the rectangle that can be drawn in the window. The upper boundary and left boundary are calculated relative to the top-left vertex of the window. In the stage model, this property should be obtained after [loadContent()](arkts-arkui-window-window-i.md#loadcontent) or [setUIContent()](arkts-arkui-window-window-i.md#setuicontent) is called to load the page content.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## focusable

```TypeScript
focusable: boolean
```

Whether the window is focusable. **true** if focusable, **false** otherwise.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## globalDisplayRect

```TypeScript
globalDisplayRect?: Rect
```

Window size in the global coordinate system. In extended screen scenarios, the top-left corner of the primary screen is used as the coordinate origin. In virtual screen scenarios, the top-left corner of the virtual screen is used as the coordinate origin. The default value is [0, 0, 0, 0].

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## id

```TypeScript
id: number
```

Window ID. The value is an integer.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isFullScreen

```TypeScript
isFullScreen: boolean
```

Whether the status bar is hidden when **isLayoutFullScreen** is set to **true**. If the status bar is hidden, the return value is **true**. In other cases, the return value is **false**.

**Type:** boolean

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isKeepScreenOn

```TypeScript
isKeepScreenOn: boolean
```

Whether the screen is always on. **true** if always on, **false** otherwise.

**Type:** boolean

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isLayoutFullScreen

```TypeScript
isLayoutFullScreen: boolean
```

Whether an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) is set for a child window. If an immersive-layout is set for the child window, the return value is **true**.

Whether an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) is set for the main window and the main window is in full-screen mode. If an immersive-layout is set for the main window and the main window is in full-screen mode, the return value is **true**.

In other cases, the return value is **false**.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isPrivacyMode

```TypeScript
isPrivacyMode: boolean
```

Whether the window is in privacy mode. **true** if the window is in privacy mode, **false** otherwise. You can call [setWindowPrivacyMode()](arkts-arkui-window-window-i.md#setwindowprivacymode) to set the privacy mode of the window.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isRoundCorner

```TypeScript
isRoundCorner: boolean
```

Whether the window has rounded corners. **true** if the window has rounded corners; **false** otherwise.

Note: This property is supported since API version 7 and deprecated since API version 9. Currently, no substitute is available.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isTransparent

```TypeScript
isTransparent: boolean
```

Whether the window background is transparent. **true** if transparent, **false** otherwise.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## name

```TypeScript
name?: string
```

Window name. The default value is an empty string.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## touchable

```TypeScript
touchable: boolean
```

Whether the window is touchable. **true** if touchable, **false** otherwise.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## type

```TypeScript
type: WindowType
```

Window type.

**Type:** [WindowType](arkts-arkui-window-windowtype-e.md)

**Since:** 7

**Deprecated since:** 26.0.0

**Substitutes:** [windowType](#windowtype)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## windowRect

```TypeScript
windowRect: Rect
```

Window size, which can be obtained from the page lifecycle [onPageShow](../arkts-components/arkts-arkui-basecustomcomponent-c.md#onpageshow) or the application lifecycle [onForeground](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md#onforeground).

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## windowType

```TypeScript
windowType?: WindowType
```

Window type

**Type:** [WindowType](arkts-arkui-window-windowtype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
