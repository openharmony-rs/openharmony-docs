# WindowAnchorInfo (System API)

Describes the anchor point information used to maintain the relative position between the level-1 child window and the main window.

**Since:** 24

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## anchorType

```TypeScript
anchorType: WindowAnchor
```

Type of the anchor point used to maintain the relative position.

**Type:** [WindowAnchor](arkts-arkui-window-windowanchor-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## offsetX

```TypeScript
offsetX?: number
```

X-axis offset between the anchor points of the child window and the main window, in px. The value must be an integer. Floating-point numbers are rounded down. The default value is **0**.

**Type:** number

**Default:** 0

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## offsetY

```TypeScript
offsetY?: number
```

Y-axis offset between the anchor points of the child window and the main window, in px. The value must be an integer. Floating-point numbers are rounded down. The default value is **0**.

**Type:** number

**Default:** 0

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
