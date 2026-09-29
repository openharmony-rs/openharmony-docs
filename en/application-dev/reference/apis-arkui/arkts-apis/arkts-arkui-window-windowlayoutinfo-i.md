# WindowLayoutInfo

```TypeScript
interface WindowLayoutInfo
```

Describes the information about the window layout.

**Since:** 15

<!--Device-window-interface WindowLayoutInfo--><!--Device-window-interface WindowLayoutInfo-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## windowAlpha

```TypeScript
windowAlpha?: number
```

The window's alpha fade level. This number is in the range 0.0 to 1.0, where 0.0 is fully transparent and 1.0 is fully opaque.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-WindowLayoutInfo-windowAlpha?: double--><!--Device-WindowLayoutInfo-windowAlpha?: double-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

Window rectangle, that is, the position and size of the window on the display.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 15

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-WindowLayoutInfo-windowRect: Rect--><!--Device-WindowLayoutInfo-windowRect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager
