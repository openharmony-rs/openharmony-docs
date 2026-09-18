# InputWindowInfo

Describes the window information of the input method keyboard.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayId

```TypeScript
displayId?: number
```

ID of the display where the soft keyboard window is located. <br> <br>**Model restriction**: This parameter can be used only in the stage model.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

Height of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

Horizontal coordinate of the upper left corner of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
name: string
```

Name of the input method keyboard window.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

Vertical coordinate of the upper left corner of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

Width of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework
