# WindowPositionParams

Describes the position of a main window to adjust its z-order.

**Since:** 26.1.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## insertAfter

```TypeScript
insertAfter: number
```

Position to adjust to. If the value is greater than 0, it is the ID of another main window, and the target window is placed below that main window. Otherwise, it is one of the [WindowPosition](arkts-arkui-window-windowposition-e.md) sentinel values, placing the window at the bottom or top of all application main windows, or toggling its global topmost state.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

ID of the main window whose z-order is to be adjusted. The window must be a main window in the current application process.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
