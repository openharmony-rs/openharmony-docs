# setScreenLockDisabled (System API)

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## setScreenLockDisabled

```TypeScript
function setScreenLockDisabled(disable: boolean, userId: number): Promise<boolean>
```

Disable screen lock showing for os account local userId. This only becomes effective when there is no password.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disable | boolean | Yes | disable or enable screen lock showing. |
| userId | number | Yes | Os account local userId. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |
| [13200002](../errorcode-screenlock.md#13200002-screen-lock-management-service-is-abnormal) | the screenlock management service is abnormal. |
