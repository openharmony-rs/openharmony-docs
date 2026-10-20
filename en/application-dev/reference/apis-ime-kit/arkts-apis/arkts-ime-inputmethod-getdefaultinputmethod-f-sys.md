# getDefaultInputMethod (System API)

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getDefaultInputMethod

```TypeScript
function getDefaultInputMethod(userId?: number): InputMethodProperty
```

Obtains the default input method of a specified user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethod-function getDefaultInputMethod(userId?: int): InputMethodProperty--><!--Device-inputMethod-function getDefaultInputMethod(userId?: int): InputMethodProperty-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided: <br> - If the caller is not an application of user 0, the value defaults to the caller's user ID. <br> - If the caller is an application of user 0, the value defaults to the foreground user ID of the home screen. |

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Default input method property object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let defaultIme: inputMethod.InputMethodProperty = inputMethod.getDefaultInputMethod(100);
  console.info('Succeeded in getting default input method, name: ' + defaultIme.name + ', id: ' + defaultIme.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getDefaultInputMethod. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->
