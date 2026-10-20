# getController

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getController

```TypeScript
function getController(): InputMethodController
```

Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance. <br> <br>Meaning/Function: Obtains the input method client controller instance of the current application, which is used for subsequent interaction with the input method (such as attaching to the input method, showing/hiding the keyboard, and synchronizing the edit box status). <br> <br>Usage scenarios: When a foreground application (such as a memo or chat application) needs to control the showing/ hiding of the input method, attach to or detach from the input method, or synchronize edit box information, it must first obtain the **InputMethodController** instance through this API. <br> <br>Use effect: Returns an **InputMethodController** instance. Subsequently, the instance can be used to call a series of APIs such as **attach**, **showTextInput**, **hideTextInput**, and **detach** to interact with the input method.

**Since:** 9

<!--Device-inputMethod-function getController(): InputMethodController--><!--Device-inputMethod-function getController(): InputMethodController-End-->

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
