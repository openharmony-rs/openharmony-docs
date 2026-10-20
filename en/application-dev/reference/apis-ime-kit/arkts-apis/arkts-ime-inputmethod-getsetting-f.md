# getSetting

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getSetting

```TypeScript
function getSetting(): InputMethodSetting
```

Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance. <br> <br>Meaning/Function: Obtains the input method setting instance, which is used for configuration management operations such as querying the input method list, subscribing to input method change events, and querying panel visibility. <br> <br>Usage scenarios: When an application needs to query the installed/activated input method list, subscribe to input method switching events, or display the input method selection dialog, it must first obtain the **InputMethodSetting** instance through this API. <br> <br>Use effect: Returns an **InputMethodSetting** instance. Subsequently, the instance can be used to call APIs such as **getInputMethods**, **listInputMethodSubtype**, and **on('imeChange')**.

**Since:** 9

<!--Device-inputMethod-function getSetting(): InputMethodSetting--><!--Device-inputMethod-function getSetting(): InputMethodSetting-End-->

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
