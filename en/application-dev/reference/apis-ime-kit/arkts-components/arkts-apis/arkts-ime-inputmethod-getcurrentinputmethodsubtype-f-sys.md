# getCurrentInputMethodSubtype (System API)

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getCurrentInputMethodSubtype

```TypeScript
function getCurrentInputMethodSubtype(userId?: number): InputMethodSubtype
```

Get the current input method subtype of a specified user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | No | the user ID. If not provided: If the caller is not a user 0 application, the value defaults to the caller's user ID. If the caller is a user 0 application, the value defaults to the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | the subtype of the current input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
```

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype(100);
  console.info('Succeeded in getting current input method subtype, id: ' + currentImeSubType.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getCurrentInputMethodSubtype. Code: ${error.code}, message: ${error.message}`);
}
```
