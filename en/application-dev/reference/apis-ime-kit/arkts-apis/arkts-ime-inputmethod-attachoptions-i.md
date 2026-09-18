# AttachOptions

Defines additional options for binding an input method.

**Since:** 23

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

Reason for requesting the keyboard.

**Type:** [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md)

**Default:** RequestKeyboardReason.NONE

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## showKeyboard

```TypeScript
showKeyboard?: boolean
```

Whether to start the input method keyboard after the self-drawing component is attached to the input method. <br> <br>- **true** means to start the input method keyboard. <br>- **false** means not to start the input method keyboard.

**Type:** boolean

**Default:** true

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework
