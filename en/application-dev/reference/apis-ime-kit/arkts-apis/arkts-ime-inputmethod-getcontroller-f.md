# getController

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getController

```TypeScript
function getController(): InputMethodController
```

Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | **InputMethodController** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800006](../errorcode-inputmethod-framework.md#12800006-input-method-controller-error) | input method controller error. Possible cause: create InputMethodController object failed. |

**Examples**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
```
