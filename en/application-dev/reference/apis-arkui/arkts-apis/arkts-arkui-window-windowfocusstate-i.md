# WindowFocusState

Describes the focus state change information of the window.

**Since:** 26.1.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## focusChangeReason

```TypeScript
focusChangeReason: FocusChangeReason
```

Reason for the focus state change.

**Type:** [FocusChangeReason](arkts-arkui-window-focuschangereason-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## isFocused

```TypeScript
isFocused: boolean
```

Whether the window gains focus. **true** if the window gains focus, **false** otherwise.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## nextFocusedWindowId

```TypeScript
nextFocusedWindowId?: number
```

ID of the next focused window. This field is valid only when the window is unfocused and the next focused window is in the same process as this window. The default value is **undefined**. The value should be an integer

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## prevFocusedWindowId

```TypeScript
prevFocusedWindowId?: number
```

ID of the previous focused window. This field is valid only when the window is focused and the previous focused window is in the same process as this window.The default value is **undefined**. The value should be an integer

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
