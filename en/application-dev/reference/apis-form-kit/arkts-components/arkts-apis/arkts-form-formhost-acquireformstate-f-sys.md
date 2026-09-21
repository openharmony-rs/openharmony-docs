# acquireFormState (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## acquireFormState

```TypeScript
function acquireFormState(want: Want, callback: AsyncCallback<formInfo.FormStateInfo>): void
```

Obtains the widget state. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | **Want** information carried to query the widget state. The information must contain the bundle name, ability name, module name, widget name, and widget dimensions. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[formInfo.FormStateInfo](arkts-form-forminfo-formstateinfo-i.md)&gt; | Yes | Callback used to return the result. If the widget state is obtained, **error** is undefined and **data** is the widget state obtained; otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |


<a id="acquireformstate-1"></a>

## acquireFormState

```TypeScript
function acquireFormState(want: Want): Promise<formInfo.FormStateInfo>
```

Obtains the widget state. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | **Want** information carried to query the widget state. The information must contain the bundle name, ability name, module name, widget name, and widget dimensions. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.FormStateInfo](arkts-form-forminfo-formstateinfo-i.md)&gt; | Promise used to return the widget state obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
