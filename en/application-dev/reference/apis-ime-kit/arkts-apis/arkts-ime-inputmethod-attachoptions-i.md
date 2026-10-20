# AttachOptions

```TypeScript
export interface AttachOptions
```

Defines additional options for binding an input method.

**Since:** 23

<!--Device-inputMethod-export interface AttachOptions--><!--Device-inputMethod-export interface AttachOptions-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

Reason for requesting keyboard input.

**Type:** [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md)

**Default:** RequestKeyboardReason.NONE

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason--><!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## showKeyboard

```TypeScript
showKeyboard?: boolean
```

Whether to show the input method keyboard after the input method is bound successfully. <br> <br>- true: Show the keyboard. <br>- false: Do not show the keyboard.

**Type:** boolean

**Default:** true

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AttachOptions-showKeyboard?: boolean--><!--Device-AttachOptions-showKeyboard?: boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
