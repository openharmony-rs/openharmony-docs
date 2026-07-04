# @ohos.ability.screenLockFileManager (Sensitive Data Access Management Under Lock Screen) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=b3b9565f7623db31a9a79d262270bc48838be44e translatedAt=2026-06-29T11:43:06.142Z pushedAt=2026-07-01T02:26:15.158Z -->

This module provides the capability of protecting app sensitive data under the lock screen, supporting requesting and releasing the permission to access app sensitive data under the lock screen, and querying the state of sensitive data keys. When the reference count of a sensitive data key reaches zero and the screen has been locked for the system-configured duration threshold, the key is destroyed, and no operations can be performed on the data. These keys can be restored only after the screen is unlocked. By calling the [acquireAccess](#screenlockfilemanageracquireaccess) API of this module, you can prevent the key from being destroyed after the screen has been locked for the system-configured duration threshold.

> **NOTE**
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This page contains only the system APIs of this module. For other public APIs, see [@ohos.ability.screenLockFileManager](js-apis-screenLockFileManager.md).
>
> - To enable the sensitive data protection under lock screen feature for an app, you need to configure the ohos.permission.PROTECT_SCREEN_LOCK_DATA permission in [requestPermissions](../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

## Modules to Import

```ts
import { screenLockFileManager } from '@kit.AbilityKit';
```

## screenLockFileManager.acquireAccess

acquireAccess(dataType: DataType): AccessStatus

Requests the permission to access a specified type of sensitive data under the lock screen synchronously. After the request is successful, the reference count of the sensitive data key increases, preventing the key from being destroyed after the screen has been locked for the system-configured duration threshold. This method must be used in pair with [releaseAccess](#screenlockfilemanagerreleaseaccess).

Before calling this API, ensure that the app has enabled the sensitive data protection under lock screen feature and that the key state queried through the [queryAppKeyState](#screenlockfilemanagerqueryappkeystate18) API is KEY_EXIST.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Parameters**

| Name | Type  | Mandatory| Description                      |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | Yes  | Type of sensitive data that is accessible on the lock screen.|

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| [AccessStatus](js-apis-screenLockFileManager.md#accessstatus) | Application status for sensitive data access under lock screen. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801 | The specified SystemCapability name was not found. |
| 29300001 | Invalid DataType. |
| 29300002 | The system ability works abnormally. |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300004 | File access is denied. |

**Example**

```ts
// Request the permission to access media data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Request access permission
    let acquireStatus = screenLockFileManager.acquireAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (acquireStatus === screenLockFileManager.AccessStatus.ACCESS_GRANTED) {
        hilog.info(0x0000, 'testTag', 'acquireAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'acquireAccess failed: %{public}s', message);
}
```

## screenLockFileManager.releaseAccess

releaseAccess(dataType: DataType): ReleaseStatus

Releases the permission to access a specified type of sensitive data under the lock screen synchronously. After the release is successful, the reference count of the sensitive data key decreases. When the reference count reaches zero, the key can be destroyed after the screen has been locked for the system-configured duration threshold.

Before calling this API, ensure that the app has enabled the sensitive data protection under lock screen feature and that the permission has been successfully requested by calling the [acquireAccess](#screenlockfilemanageracquireaccess) API first.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Parameters**

| Name | Type  | Mandatory| Description                      |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | Yes | Sensitive data type accessed under lock screen. The dataType must be consistent with the dataType used in the acquireAccess API. |

**Return value**

| Type                                                        | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [ReleaseStatus](js-apis-screenLockFileManager.md#releasestatus) | Release status of sensitive data access permission under lock screen. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | The specified SystemCapability name was not found.           |
| 29300001 | Invalid DataType.                                           |
| 29300002 | The system ability works abnormally.                          |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300005 | File access was not acquired.                                |

**Example**

```ts
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

## screenLockFileManager.queryAppKeyState<sup>18+</sup>

queryAppKeyState(dataType: DataType): KeyStatus

Queries the state of a specified type of sensitive data key under the lock screen synchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**System capability**: SystemCapability.Security.ScreenLockFileManager

**Parameters**

| Name | Type  | Mandatory| Description                      |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | Yes  | Type of sensitive data that is accessible on the lock screen.|

**Return value**

| Type                                                        | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [KeyStatus](js-apis-screenLockFileManager.md#keystatus18) | Status of the key for sensitive data under lock screen. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [ohos.screenLockFileManager Error Codes](errorcode-screenLockFileManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | The specified SystemCapability name was not found.           |
| 29300001 | Invalid DataType.                                           |
| 29300002 | The system ability works abnormally.                          |

**Example**

```ts
// Obtain the state of access permissions for media data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Query the key status
    let keyStatus = screenLockFileManager.queryAppKeyState(screenLockFileManager.DataType.MEDIA_DATA);
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