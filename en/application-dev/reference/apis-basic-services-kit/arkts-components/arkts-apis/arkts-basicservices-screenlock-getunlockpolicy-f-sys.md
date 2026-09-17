# getUnlockPolicy (System API)

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## getUnlockPolicy

```TypeScript
function getUnlockPolicy(userId: number): UnlockPolicy
```

Obtains the authentication policy used to unlock the screen.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | Local user ID of the OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| [UnlockPolicy](arkts-basicservices-screenlock-unlockpolicy-e-sys.md) | The unlock policy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed: applications that are not system applications cannot use system API. |
| [13200002](../errorcode-screenlock.md#13200002-screen-lock-management-service-is-abnormal) | The screen lock management service is abnormal. |
| 13200004 | The userId is not the same as the caller, and the caller is not authorized. |
