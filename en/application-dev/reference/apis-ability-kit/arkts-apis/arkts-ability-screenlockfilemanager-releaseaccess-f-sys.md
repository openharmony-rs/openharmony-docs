# releaseAccess (System API)

## Modules to Import

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

<a id="releaseaccess-1"></a>

## releaseAccess

```TypeScript
function releaseAccess(dataType: DataType): ReleaseStatus
```

Releases the permission to access a specified type of sensitive data under the lock screen synchronously. After the release is successful, the reference count of the sensitive data key decreases. When the reference count reaches zero, the key can be destroyed after the screen has been locked for the system-configured duration threshold.

Before calling this API, ensure that the app has enabled the sensitive data protection under lock screen feature and that the permission has been successfully requested by calling the [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md) API first.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**System capability:** SystemCapability.Security.ScreenLockFileManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-ability-screenlockfilemanager-datatype-e.md) | Yes | Type of sensitive data that is accessible on the lock screen. The dataType must be consistent with the dataType used in the acquireAccess API. |

**Return value:**

| Type | Description |
| --- | --- |
| [ReleaseStatus](arkts-ability-screenlockfilemanager-releasestatus-e.md) | Release status of the access permission for sensitive data under lock screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameter is left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [29300001](../errorcode-screenLockFileManager.md#29300001-invalid-parameter) | Invalid DataType. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-system-service-abnormal) | The system ability works abnormally. |
| [29300003](../errorcode-screenLockFileManager.md#29300003-sensitive-data-access-management-under-lock-screen-is-not-enabled) | The application is not enabled the data protection under lock screen. |
| [29300005](../errorcode-screenLockFileManager.md#29300005-permission-to-access-sensitive-data-on-the-lock-screen-is-not-requested) | File access was not acquired. |

**Examples**

```TypeScript
// Release the permission to access media data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Release access permission
    let releaseStatus = screenLockFileManager.releaseAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (releaseStatus === screenLockFileManager.ReleaseStatus.RELEASE_GRANTED) {
        hilog.info(0x0000, 'testTag', 'releaseAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'releaseAccess failed: %{public}s', message);
}
```
