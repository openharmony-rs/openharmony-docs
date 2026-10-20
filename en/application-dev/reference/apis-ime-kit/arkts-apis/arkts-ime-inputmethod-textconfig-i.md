# TextConfig

```TypeScript
export interface TextConfig
```

Describes the configuration of the edit box.

**Since:** 10

<!--Device-inputMethod-export interface TextConfig--><!--Device-inputMethod-export interface TextConfig-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## capitalizeMode

```TypeScript
capitalizeMode?: CapitalizeMode
```

Capitalization mode set for the text box. If no value is set or an invalid value is set, no initial capitalization is performed by default.

**Type:** [CapitalizeMode](arkts-ime-inputmethod-capitalizemode-e.md)

**Default:** CapitalizeMode.NONE

**Since:** 20

<!--Device-TextConfig-capitalizeMode?: CapitalizeMode--><!--Device-TextConfig-capitalizeMode?: CapitalizeMode-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## cursorInfo

```TypeScript
cursorInfo?: CursorInfo
```

Cursor information.

**Type:** [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md)

**Since:** 10

<!--Device-TextConfig-cursorInfo?: CursorInfo--><!--Device-TextConfig-cursorInfo?: CursorInfo-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## inputAttribute

```TypeScript
inputAttribute: InputAttribute
```

Text box attribute.

**Type:** [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md)

**Since:** 10

<!--Device-TextConfig-inputAttribute: InputAttribute--><!--Device-TextConfig-inputAttribute: InputAttribute-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## newEditBox

```TypeScript
newEditBox?: boolean
```

Whether it is a new text box. The value **true** indicates a new text box, and **false** indicates a non-new text box. The default value is **false**.

**Type:** boolean

**Since:** 20

<!--Device-TextConfig-newEditBox?: boolean--><!--Device-TextConfig-newEditBox?: boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## selection

```TypeScript
selection?: Range
```

Selected text range.

**Type:** [Range](arkts-ime-inputmethod-range-i.md)

**Since:** 10

<!--Device-TextConfig-selection?: Range--><!--Device-TextConfig-selection?: Range-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## windowId

```TypeScript
windowId?: number
```

ID of the window where the text box is located. This parameter must be an integer. <br> <br>It is recommended that you use [getWindowProperties](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window ID attribute.

**Type:** number

**Since:** 10

<!--Device-TextConfig-windowId?: int--><!--Device-TextConfig-windowId?: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
