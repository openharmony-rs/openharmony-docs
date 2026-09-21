# acquireAccess

## Modules to Import

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

## acquireAccess

```TypeScript
function acquireAccess(): AccessStatus
```

Requests the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the request is successful, the reference count of the sensitive data key increases, preventing the key from being destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold. This method must be used in pair with [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md).

Before calling this API, ensure that the app has enabled the sensitive data protection function under the lock screen, and that the key status queried through the [queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f.md) API is KEY_EXIST.

**Since:** 12

**System capability:** SystemCapability.Security.ScreenLockFileManager

**Return value:**

| Type | Description |
| --- | --- |
| [AccessStatus](arkts-ability-screenlockfilemanager-accessstatus-e.md) | Application status for access permission for sensitive data under lock screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-system-service-abnormal) | The system ability works abnormally. |
| [29300003](../errorcode-screenLockFileManager.md#29300003-sensitive-data-access-management-under-lock-screen-is-not-enabled) | The application is not enabled the data protection under lock screen. |
| [29300004](../errorcode-screenLockFileManager.md#29300004-permission-to-access-sensitive-data-on-the-lock-screen-has-been-revoked) | File access is denied. |

**Examples**

```TypeScript
// Request the permission to access sensitive data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Request access permission
    let acquireStatus = screenLockFileManager.acquireAccess();
    if (acquireStatus === screenLockFileManager.AccessStatus.ACCESS_GRANTED) {
        hilog.info(0x0000, 'testTag', 'acquireAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'acquireAccess failed: %{public}s', message);
}
```
