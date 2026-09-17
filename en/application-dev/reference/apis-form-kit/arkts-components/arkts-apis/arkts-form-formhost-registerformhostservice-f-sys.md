# registerFormHostService (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## registerFormHostService

```TypeScript
function registerFormHostService(service: formInfo.FormHostServiceInfo): Promise<string>
```

Register the form host service info.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| service | [formInfo.FormHostServiceInfo](arkts-form-forminfo-formhostserviceinfo-i-sys.md) | Yes | Identifies service info registered to form management service. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the service Id of the form host service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
