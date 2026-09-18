# MultiScreenPositionOptions (System API)

Describes the screen position information.

**Since:** 13

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## id

```TypeScript
id: number
```

Screen ID. The value must be a positive integer. Any non-positive integer values will be considered invalid and result in an error.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## startX

```TypeScript
startX: number
```

Start X coordinate of the screen. The top-left vertex of the bounding rectangle formed by the two screens is used as the origin, with the positive direction being rightwards. in px. The value must be a non-negative integer. Any other values will be considered invalid and result in an error.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## startY

```TypeScript
startY: number
```

Start Y coordinate of the screen. The top-left vertex of the bounding rectangle formed by the two screens is used as the origin, with the positive direction being downwards. in px. The value must be a non-negative integer. Any other values will be considered invalid and result in an error.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
