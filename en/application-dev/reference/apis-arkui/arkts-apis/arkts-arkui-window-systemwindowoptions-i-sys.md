# SystemWindowOptions (System API)

Describes the parameters for creating a system window.

**Since:** 14

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## windowType

```TypeScript
windowType: WindowType
```

Window type. There is no default value. If null is passed in, the window fails to be created. **TYPE_DIALOG** is not supported.

**Type:** [WindowType](arkts-arkui-window-windowtype-e.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
