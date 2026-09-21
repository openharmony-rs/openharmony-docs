# switchCurrentInputMethodSubtype

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## switchCurrentInputMethodSubtype

```TypeScript
function switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback<boolean>): void
```

Switches to another subtype of this input method. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> - In API version 9, this API can only be called by system applications granted the **ohos.permission.CONNECT_IME_ABILITY** permission. <br><br>
> - In API version 10, this API can only be called by system applications and the current input method application, and the **ohos.permission.CONNECT_IME_ABILITY** permission is required. <br><br>
> - Since API version 11, this API can only be called by the current input method application.

**Since:** 9

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.CONNECT_IME_ABILITY

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | Yes | Target input method subtype. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object. |

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

let extra: Record<string, string> = {}
// Refer to the InputMethodSubtype parameter description.
inputMethod.switchCurrentInputMethodSubtype({
  id: "ServiceExtAbility",
  label: "",
  name: "com.example.keyboard",
  mode: "upper",
  locale: "",
  language: "",
  icon: "",
  iconId: 0,
  extra: extra
}, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching currentInputMethodSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodSubtype');
  }
});
```


<a id="switchcurrentinputmethodsubtype-1"></a>

## switchCurrentInputMethodSubtype

```TypeScript
function switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise<boolean>
```

Switches to another subtype of this input method. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> - In API version 9, this API can only be called by system applications granted the **ohos.permission.CONNECT_IME_ABILITY** permission. <br><br>
> - In API version 10, this API can only be called by system applications and the current input method application, and the **ohos.permission.CONNECT_IME_ABILITY** permission is required. <br><br>
> - Since API version 11, this API can only be called by the current input method application.

**Since:** 9

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.CONNECT_IME_ABILITY

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | Yes | Target input method subtype. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the switching is successful, and **false** means the opposite. |

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

let extra: Record<string, string> = {}
// Refer to the InputMethodSubtype parameter description.
inputMethod.switchCurrentInputMethodSubtype({
  id: "ServiceExtAbility",
  label: "",
  name: "com.example.keyboard",
  mode: "upper",
  locale: "",
  language: "",
  icon: "",
  iconId: 0,
  extra: extra
}).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching currentInputMethodSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodSubtype.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
});
```
