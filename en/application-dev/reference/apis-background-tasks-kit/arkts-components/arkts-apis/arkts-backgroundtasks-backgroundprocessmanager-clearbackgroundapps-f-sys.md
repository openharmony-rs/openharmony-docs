# clearBackgroundApps (System API)

## Modules to Import

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## clearBackgroundApps

```TypeScript
function clearBackgroundApps(clearType: ClearType): Promise<void>
```

One-tap background app cleanup

**Since:** 26.1.0

**Required permissions:** ohos.permission.CLEAR_BACKGROUND_APPS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clearType | [ClearType](arkts-backgroundtasks-backgroundprocessmanager-cleartype-e-sys.md) | Yes | the type of clearing background apps. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [31800002](../errorcode-backgroundProcessManager.md#31800002-invalid-parameter) | Parameter error. |
