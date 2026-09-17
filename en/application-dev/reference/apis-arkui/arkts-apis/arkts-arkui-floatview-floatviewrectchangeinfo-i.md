# FloatViewRectChangeInfo

Provides the rectangle area change information of the float view.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## reason

```TypeScript
reason: string
```

Reason for the change of the rectangle area of the float view. The reasons and their meanings are as follows:

**"POSITION_CHANGE"**: The position changes.

**"SIZE_CHANGE"**: The size changes.

**"RECT_CHANGE"**: Both the position and size change.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: window.Rect
```

Rectangle area of the float view.

**Type:** [window.Rect](arkts-arkui-window-rect-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## windowScale

```TypeScript
windowScale: number
```

Scale factor of the float view.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
