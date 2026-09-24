# @ohos.ability.screenLockFileManager(Sensitive Data Access Management Under Lock Screen)

This module provides the capability to protect app sensitive data under the lock screen, supporting requesting and releasing access permissions for sensitive data under the lock screen, as well as querying the status of sensitive data keys. When the reference count of a sensitive data key reaches zero and the screen has been locked for a duration reaching the system-configured lock duration threshold, the key is destroyed, and operations on that data become impossible. These keys can be restored only after the screen is unlocked. By calling the [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md) API of this module, you can prevent the key from being destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold.

> **NOTE:** 
> 
> - To enable the sensitive data protection function under the lock screen for an app, you need to configure the ohos.permission.PROTECT_SCREEN_LOCK_DATA permission in [requestPermissions](../../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

**Since:** 12

**System capability:** SystemCapability.Security.ScreenLockFileManager

## Modules to Import

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md) | Requests the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the request is successful, the reference count of the sensitive data key increases, preventing the key from being destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold. This method must be used in pair with [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md). |
| [queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f.md) | Queries the status of the caller app's sensitive data key under the lock screen in synchronous mode. |
| [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md) | Releases the access permission for the caller app's sensitive data under the lock screen in synchronous mode. After the release is successful, the reference count of the sensitive data key decreases. When the count reaches zero, the key can be destroyed after the screen has been locked for a duration reaching the system-configured lock duration threshold. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f-sys.md#acquireaccess-1) | Requests the permission to access a specified type of sensitive data under the lock screen synchronously. After the request is successful, the reference count of the sensitive data key increases, preventing the key from being destroyed after the screen has been locked for the system-configured duration threshold. This method must be used in pair with [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md). |
| [queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f-sys.md#queryappkeystate-1) | Queries the status of a specified type of sensitive data key under the lock screen synchronously. |
| [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f-sys.md#releaseaccess-1) | Releases the permission to access a specified type of sensitive data under the lock screen synchronously. After the release is successful, the reference count of the sensitive data key decreases. When the reference count reaches zero, the key can be destroyed after the screen has been locked for the system-configured duration threshold. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AccessStatus](arkts-ability-screenlockfilemanager-accessstatus-e.md) | Enumerates the statuses for requesting access permissions for sensitive data under the lock screen. |
| [DataType](arkts-ability-screenlockfilemanager-datatype-e.md) | Enumerates the types of sensitive data that can be accessed under the lock screen. |
| [KeyStatus](arkts-ability-screenlockfilemanager-keystatus-e.md) | Enumerates the statuses of sensitive data keys under the lock screen. |
| [ReleaseStatus](arkts-ability-screenlockfilemanager-releasestatus-e.md) | Enumerates the statuses for releasing access permissions for sensitive data under the lock screen. |
