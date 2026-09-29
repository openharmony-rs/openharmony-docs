# RotationChangeInfo

```TypeScript
interface RotationChangeInfo
```

Describes the window information obtained during window rotation changes.

**Since:** 19

<!--Device-window-interface RotationChangeInfo--><!--Device-window-interface RotationChangeInfo-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId: number
```

ID of the screen where the window is located.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeInfo-displayId: long--><!--Device-RotationChangeInfo-displayId: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## displayRect

```TypeScript
displayRect: Rect
```

Size of the rectangle after the screen where the window is located is rotated.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeInfo-displayRect: Rect--><!--Device-RotationChangeInfo-displayRect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager

## orientation

```TypeScript
orientation: number
```

Display orientation of the window.

- **0**: portrait.  
- **1**: reverse landscape.  
- **2**: reverse portrait.  
- **3**: landscape.

Note that the orientation here is different from the orientation property of the display object.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeInfo-orientation: int--><!--Device-RotationChangeInfo-orientation: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## type

```TypeScript
type: RotationChangeType
```

Type of window rotation event.

**Type:** [RotationChangeType](arkts-arkui-window-rotationchangetype-e.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-RotationChangeInfo-type: RotationChangeType--><!--Device-RotationChangeInfo-type: RotationChangeType-End-->

**System capability:** SystemCapability.Window.SessionManager
