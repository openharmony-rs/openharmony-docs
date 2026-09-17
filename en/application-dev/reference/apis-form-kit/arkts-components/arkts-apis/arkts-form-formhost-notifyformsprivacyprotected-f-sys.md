# notifyFormsPrivacyProtected (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## notifyFormsPrivacyProtected

```TypeScript
function notifyFormsPrivacyProtected(
    formIds: Array<string>,
    isProtected: boolean,
    callback: AsyncCallback<void>
  ): void
```

Notifies that the privacy protection status of the specified widgets changes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | ID of the widgets. |
| isProtected | boolean | Yes | Whether a widget requires privacy protection.<br>**true**: The widget requires privacy protection. <br>**false**: The widget does not require privacy protection. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If privacy protection is set successfully, **error** is undefined; otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |


## notifyFormsPrivacyProtected

```TypeScript
function notifyFormsPrivacyProtected(formIds: Array<string>, isProtected: boolean): Promise<void>
```

Notifies that the privacy protection status of the specified widgets changes. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | ID of the widgets. |
| isProtected | boolean | Yes | Whether a widget requires privacy protection.<br>**true**: The widget requires privacy protection. <br>**false**: The widget does not require privacy protection. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
