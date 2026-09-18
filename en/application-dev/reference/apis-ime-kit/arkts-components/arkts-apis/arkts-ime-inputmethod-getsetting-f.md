# getSetting

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getSetting

```TypeScript
function getSetting(): InputMethodSetting
```

Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | **InputMethodSetting** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800007](../errorcode-inputmethod-framework.md#12800007-input-method-setter-error) | input method setter error. Possible cause: create InputMethodSetting object failed. |

**Examples**

```TypeScript
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
```
