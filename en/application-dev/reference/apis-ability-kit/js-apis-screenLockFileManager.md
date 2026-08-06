# @ohos.ability.screenLockFileManager (Sensitive Data Access Management Under Lock Screen)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=b3b9565f7623db31a9a79d262270bc48838be44e translatedAt=2026-06-29T11:43:11.654Z pushedAt=2026-07-01T08:29:24.653Z -->

This module provides the capability to protect app sensitive data under the lock screen, supporting requesting and releasing access permissions for sensitive data under the lock screen, as well as querying the status of sensitive data keys. When the reference count of a sensitive data key reaches zero and the screen has been locked for a duration reaching the system-configured lock duration threshold, the key is destroyed, and operations on that data become impossible. These keys can be restored only after the screen is unlocked. By calling the [acquireAccess](#screenlockfilemanageracquireaccess) API of this module, you can prevent the key from being destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold.

> **NOTE**
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - To enable the sensitive data protection function under the lock screen for an app, you need to configure the ohos.permission.PROTECT_SCREEN_LOCK_DATA permission in [requestPermissions](../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

## Modules to Import

```ts
import { screenLockFileManager } from '@kit.AbilityKit';
```

## DataType

Enumerates the types of sensitive data that can be accessed under the lock screen.

**System capability:** SystemCapability.Security.ScreenLockFileManager

| Name      | Value        | Description          |
| ---------- | ---------- | -------------- |
| MEDIA_DATA | 0x00000001 | Media data type. |
| ALL_DATA   | 0xffffffff | All sensitive data types. |

## AccessStatus

Enumerates the statuses for requesting access permissions for sensitive data under the lock screen.

**System capability:** SystemCapability.Security.ScreenLockFileManager

| Name          | Value  | Description                    |
| -------------- | ---- | ------------------------ |
| ACCESS_DENIED  | -1   | The request for access permission for sensitive data under lock screen is denied. |
| ACCESS_GRANTED | 0    | The request for access permission for sensitive data under lock screen is granted. |

## ReleaseStatus

Enumerates the statuses for releasing access permissions for sensitive data under the lock screen.

**System capability:** SystemCapability.Security.ScreenLockFileManager

| Name| Value| Description|
|-----------------|----|----|
| RELEASE_DENIED | -1 | Release of access permission for sensitive data under lock screen is denied. |
| RELEASE_GRANTED | 0 | Release of access permission for sensitive data under lock screen is granted. |

## KeyStatus<sup>18+</sup>

Enumerates the statuses of sensitive data keys under the lock screen.

**System capability:** SystemCapability.Security.ScreenLockFileManager

| Name| Value| Description|
|-----------------|----|----|
| KEY_NOT_EXIST | -2 | The key does not exist. This status indicates that the app has not enabled the sensitive data protection function under lock screen, or the protection function is unavailable on the current device. |
| KEY_RELEASED | -1 | The key has been released. This status indicates that sensitive data under lock screen cannot be operated. |
| KEY_EXIST | 0 | The key exists. This status indicates that sensitive data under lock screen can be operated normally. |

## screenLockFileManager.acquireAccess

acquireAccess(): AccessStatus

Requests the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the request is successful, the reference count of the sensitive data key increases, preventing the key from being destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold. This method must be used in pair with [releaseAccess](#screenlockfilemanagerreleaseaccess).

Before calling this API, ensure that the app has enabled the sensitive data protection function under the lock screen, and that the key status queried through the [queryAppKeyState](#screenlockfilemanagerqueryappkeystate18) API is KEY_EXIST.

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| [AccessStatus](#accessstatus) | Application status for access permission for sensitive data under lock screen. |

**Error codes**

For detailed introduction of the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801 | The specified SystemCapability name was not found. |
| 29300002 | The system ability works abnormally. |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300004 | File access is denied. |

**Example**

```ts
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

## screenLockFileManager.releaseAccess

releaseAccess(): ReleaseStatus

Releases the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the release is successful, the reference count of the sensitive data key decreases. When the count reaches zero, the key can be destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold.

Before calling this API, ensure that the app has enabled the sensitive data protection function under the lock screen, and that the [acquireAccess](#screenlockfilemanageracquireaccess) API has been called to request the permission successfully first.

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Return value**

| Type                           | Description                          |
| ------------------------------- | ------------------------------ |
| [ReleaseStatus](#releasestatus) | Release status of the access permission for sensitive data under lock screen. |

**Error codes**

For detailed introduction of the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | The specified SystemCapability name was not found.           |
| 29300002 | The system ability works abnormally.                          |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300005 | File access was not acquired. |

**Example**

```ts
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

## screenLockFileManager.queryAppKeyState<sup>18+</sup>

queryAppKeyState(): KeyStatus

Queries the status of the caller app's sensitive data key under the lock screen in synchronous mode.

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Return value**

| Type                           | Description                          |
| ------------------------------- | ------------------------------ |
| [KeyStatus](#keystatus18) | Status of the key for sensitive data under lock screen. |

**Error codes**

For detailed introduction of the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | The specified SystemCapability name was not found.           |
| 29300002 | The system ability works abnormally.                          |

**Example**

```ts
// Obtain the state of access permissions for sensitive data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Query the key status
    let keyStatus = screenLockFileManager.queryAppKeyState();
    // Determine the key status and handle different situations
    if (keyStatus === screenLockFileManager.KeyStatus.KEY_NOT_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key does not exist.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_RELEASED) {
        hilog.info(0x0000, 'testTag', 'Key has been released.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key exists.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'queryAppKeyState failed: %{public}s', message);
}
```