# RotationChangeResult

```TypeScript
interface RotationChangeResult
```

Describes the information returned by the application during window rotation changes. The system uses the information to adjust the size of the current window rectangle. If the returned information is about the rotation change of the main window, the system does not change the size of the main window.

There are limitations on the size of application windows and system windows. For details about specific restrictions and rules, see [resize](arkts-arkui-window-window-i.md#resize).

**Since:** 19

<!--Device-window-interface RotationChangeResult--><!--Device-window-interface RotationChangeResult-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## rectType

```TypeScript
rectType: RectType
```

Type of window rectangle coordinate system.

**Type:** [RectType](arkts-arkui-window-recttype-e.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeResult-rectType: RectType--><!--Device-RotationChangeResult-rectType: RectType-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

Information about the window's rectangle relative to the screen or parent window coordinate system.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeResult-windowRect: Rect--><!--Device-RotationChangeResult-windowRect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager
