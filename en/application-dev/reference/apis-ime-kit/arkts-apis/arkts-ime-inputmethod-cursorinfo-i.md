# CursorInfo

```TypeScript
export interface CursorInfo
```

Cursor information.

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

ID of the display where the cursor is located. This parameter must be an integer, with a minimum value of 0 and a default value of 0. <br> <br>**Initial version:** 26.0.0 <br> <br>**Model restriction:** This parameter can be used only in the Stage model.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CursorInfo-displayId?: long--><!--Device-CursorInfo-displayId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

Height of the cursor, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen height.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-height: double--><!--Device-CursorInfo-height: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

Horizontal coordinate of the cursor, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen width.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-left: double--><!--Device-CursorInfo-left: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

Vertical coordinate of the cursor, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen height.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-top: double--><!--Device-CursorInfo-top: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

Width of the cursor, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen width.

**Type:** number

**Since:** 10

<!--Device-CursorInfo-width: double--><!--Device-CursorInfo-width: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
