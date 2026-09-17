# unregisterFormHostService (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## unregisterFormHostService

```TypeScript
function unregisterFormHostService(serviceId: string): Promise<void>
```

Unregister the form host service info.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceId | string | Yes | Identifies service Id of the form host service. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501019](../errorcode-form.md#16501019-unable-to-unregister-the-widget-service-not-registered-by-the-current-application) | A form service not owned by you cannot be unregistered. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
