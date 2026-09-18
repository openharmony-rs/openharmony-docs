# SystemBarTintState (System API)

Describes the callback for the current system bar.

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId: number
```

ID of the screen where the window is located. The value must be an integer.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## regionTint

```TypeScript
regionTint: Array<SystemBarRegionTint>
```

All system bar information that has been changed.

**Type:** Array&lt;[SystemBarRegionTint](arkts-arkui-window-systembarregiontint-i-sys.md)&gt;

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
