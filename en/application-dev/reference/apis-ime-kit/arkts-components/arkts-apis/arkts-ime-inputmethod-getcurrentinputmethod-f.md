# getCurrentInputMethod

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getCurrentInputMethod

```TypeScript
function getCurrentInputMethod(): InputMethodProperty
```

Obtains the current input method. This API returns the result synchronously.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | **InputmethodProperty** instance of the current input method. |

**Examples**

```TypeScript
let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
```
