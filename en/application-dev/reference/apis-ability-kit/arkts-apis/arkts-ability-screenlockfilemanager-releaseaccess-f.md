# releaseAccess

## Modules to Import

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

## releaseAccess

```TypeScript
function releaseAccess(): ReleaseStatus
```

Releases the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the release is successful, the reference count of the sensitive data key decreases. When the count reaches zero, the key can be destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold.

Before calling this API, ensure that the app has enabled the sensitive data protection function under the lock screen, and that the [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md) API has been called to request the permission successfully first.

**Since:** 12

**System capability:** SystemCapability.Security.ScreenLockFileManager

**Return value:**

| Type | Description |
| --- | --- |
| [ReleaseStatus](arkts-ability-screenlockfilemanager-releasestatus-e.md) | Release status of the access permission for sensitive data under lock screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-system-service-abnormal) | The system ability works abnormally. |
| [29300003](../errorcode-screenLockFileManager.md#29300003-sensitive-data-access-management-under-lock-screen-is-not-enabled) | The application is not enabled the data protection under lock screen. |
| [29300005](../errorcode-screenLockFileManager.md#29300005-permission-to-access-sensitive-data-on-the-lock-screen-is-not-requested) | File access was not acquired. |

**Examples**

```TypeScript
// Release the permission to access sensitive data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Release access permission
    let releaseStatus = screenLockFileManager.releaseAccess();
    if (releaseStatus === screenLockFileManager.ReleaseStatus.RELEASE_GRANTED) {
        hilog.info(0x0000, 'testTag', 'releaseAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'releaseAccess failed: %{public}s', message);
}
```
