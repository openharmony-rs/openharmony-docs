# WindowLayoutInfo

Describes the information about the window layout.

**Since:** 15

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

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

Window rectangle, that is, the position and size of the window on the display.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager
