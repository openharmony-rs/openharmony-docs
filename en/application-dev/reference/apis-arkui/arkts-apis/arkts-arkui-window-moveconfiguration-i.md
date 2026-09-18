# MoveConfiguration

Describes the window movement configuration.

**Since:** 15

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId?: number
```

Target display ID. The value must be an integer. If a non-integer is passed in, the value is rounded down. If this parameter is passed in, the window is positioned relative to the top-left corner of the target display. If this parameter is left empty or the target display ID does not exist, the window is positioned relative to the top-left corner of the current display.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager
