# CursorInfo

```TypeScript
export interface CursorInfo
```

Represents the cursor information.

**Since:** 10

<!--Device-inputMethod-export interface CursorInfo--><!--Device-inputMethod-export interface CursorInfo-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayId

```TypeScript
displayId?: number
```

ID of the monitor where the cursor is located.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CursorInfo-displayId?: long--><!--Device-CursorInfo-displayId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

Height of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-height: double--><!--Device-CursorInfo-height: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

Horizontal coordinate of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-left: double--><!--Device-CursorInfo-left: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

Vertical coordinate of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-top: double--><!--Device-CursorInfo-top: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

Width of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-width: double--><!--Device-CursorInfo-width: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
