# getCurrentInputMethodSubtype

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getCurrentInputMethodSubtype

```TypeScript
function getCurrentInputMethodSubtype(): InputMethodSubtype
```

Obtains the current input method subtype.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | Current input method subtype. |

**Examples**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
```
