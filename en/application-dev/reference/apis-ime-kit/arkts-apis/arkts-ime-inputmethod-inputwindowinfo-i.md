# InputWindowInfo

```TypeScript
export interface InputWindowInfo
```

Window information of the input method soft keyboard (system API extended properties).

**Since:** 10

<!--Device-inputMethod-export interface InputWindowInfo--><!--Device-inputMethod-export interface InputWindowInfo-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayId

```TypeScript
displayId?: number
```

ID of the screen where the input method soft keyboard window is located. <br> <br>**Model restriction:** This parameter can be used only in the stage model.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputWindowInfo-displayId?: long--><!--Device-InputWindowInfo-displayId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

Height of the input method window, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen height.

**Type:** number

**Since:** 10

<!--Device-InputWindowInfo-height: long--><!--Device-InputWindowInfo-height: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

Horizontal coordinate of the upper left vertex of the input method window, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen width.

**Type:** number

**Since:** 10

<!--Device-InputWindowInfo-left: int--><!--Device-InputWindowInfo-left: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
name: string
```

Name of the input method window.

**Type:** string

**Since:** 10

<!--Device-InputWindowInfo-name: string--><!--Device-InputWindowInfo-name: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

Vertical coordinate of the upper left vertex of the input method window, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen height.

**Type:** number

**Since:** 10

<!--Device-InputWindowInfo-top: int--><!--Device-InputWindowInfo-top: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

Width of the input method window, in px. This parameter must be an integer, with a minimum value of 0 and a maximum value of the current screen width.

**Type:** number

**Since:** 10

<!--Device-InputWindowInfo-width: long--><!--Device-InputWindowInfo-width: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
