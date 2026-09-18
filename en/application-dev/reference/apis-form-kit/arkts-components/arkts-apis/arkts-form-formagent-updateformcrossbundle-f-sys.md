# updateFormCrossBundle (System API)

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## updateFormCrossBundle

```TypeScript
function updateFormCrossBundle(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>
```

Updates a widget by cross bundle. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.UPDATE_FORM_CROSS_BUNDLE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | ID of the widget to update. |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | Yes | Data to be used for the update. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | Possible cause IPC connection error. Such as the remote object dose not exist. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Possible cause Service State error. Such as the form is recovering. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | Possible cause internal functional error. Such as virtualization failed. |
| [16501001](../errorcode-form.md#16501001-widget-id-not-exist) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-widget-not-operatable) | The form to be operated has been deleted already. |
| [16501007](../errorcode-form.md#16501007-untrusted-widget) | The form to be operated is not trusted. |
