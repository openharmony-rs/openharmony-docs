# StartMovingOptions (System API)

Optional configuration for startMovingWithOptions.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## avoidRect

```TypeScript
avoidRect?: Rect
```

The avoidance rect of window during drag-moving. If unspecified, the system defaults to the following avoidance behavior: Free window state: 1.Main windows, subWindows and dialog windows can be dragged beyond the screen bounds and will spring back on release. 2.Other windows can be dragged beyond the screen bounds without springing back. Non-free window state: 1.System windows can be dragged beyond the main window bounds and the screen bounds without springing back. 2.When the main window is fullscreen, subWindows and dialog windows can be dragged beyond it without springing back. 3.When the main window is not fullscreen, subWindows and dialog windows can be dragged beyond it and will spring back on release.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## needFocused

```TypeScript
needFocused?: boolean
```

Indicates whether the window needs to be focused when moving starts.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
