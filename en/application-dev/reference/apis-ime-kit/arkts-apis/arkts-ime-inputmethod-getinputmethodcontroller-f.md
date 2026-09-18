# getInputMethodController

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getInputMethodController

```TypeScript
function getInputMethodController(): InputMethodController
```

Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getController](arkts-ime-inputmethod-getcontroller-f.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | Current **InputMethodController** instance. |

**Examples**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getInputMethodController();
```
