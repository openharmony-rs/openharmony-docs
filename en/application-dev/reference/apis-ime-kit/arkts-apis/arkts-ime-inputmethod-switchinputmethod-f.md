# switchInputMethod

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## switchInputMethod

```TypeScript
function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void
```

Switches the input method. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Switches the current input method to the specified target input method. <br> <br>Usage scenarios: Used when the current input method application needs to switch to another input method (for example, when the user selects a new input method in the input method settings). <br> <br>Use effect: On success, the system switches the current input method to the target input method, and the target input method becomes the new current input method; on failure, the current input method remains unchanged.

**Since:** 9

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void--><!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Yes | Target input method.Usage scenario: specifies the target input method to switch to, uniquely determined by **name** and **id**.<br>Note: only the **name** and **id** fields need to be filled in to uniquely specify an input method; optional fields such as **label** and **icon** do not need to be filled in. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback function. When the input method switch succeeds, **err** is **undefined** and data is **true**; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 9 - 10 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-configuration-persistence-failure) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
});
```


## switchInputMethod

```TypeScript
function switchInputMethod(target: InputMethodProperty): Promise<boolean>
```

Switches the input method. This API uses a promise to return the result. <br> <br>Meaning/Function: Switches the current input method to the specified target input method. <br> <br>Usage scenarios: Used when the current input method application needs to switch to another input method. <br> <br>Use effect: On success, the system switches the current input method to the target input method; on failure, the current input method remains unchanged.

**Since:** 9

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty): Promise<boolean>--><!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Yes | Target input method.Usage scenario: specifies the target input method to switch to, uniquely determined by **name** and **id**.<br>Note: only the **name** and **id** fields need to be filled in to uniquely specify an input method. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise object. When resolved, returns **true** if the input method is switched successfully, and returns **false** if the input method fails to be switched; when rejected, returns an error object, indicating that an error occurs during input method switching. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 9 - 10 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-configuration-persistence-failure) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
});
```
