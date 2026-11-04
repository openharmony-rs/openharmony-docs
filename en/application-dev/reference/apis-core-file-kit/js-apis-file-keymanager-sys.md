# @ohos.file.keyManager (User Key Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @gzhuangzhuang-->
<!--Designer: @renguang1116; @wang_zhangjun-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=702709eb5022bd8c1dd4f0c8a857431c342bafb0 translatedAt=2026-11-03T04:34:45.323Z pushedAt=2026-11-04T03:11:33.528Z nl=1 -->

This module provides user key management capabilities. It currently supports synchronously unloading the key of a specified user when the user locks the screen, meeting the requirement of lock screen applications to protect user data security when the device is locked. User keys are related to the encryption protection of user data. In scenarios such as user screen lock, the keys need to be unloaded to manage the encryption state of the data.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module.

## Modules to Import

```ts
import { keyManager } from '@kit.CoreFileKit';
```

## keyManager.deactivateUserKey

deactivateUserKey(userId: number):void

When the user locks the screen, synchronously unloads the key corresponding to the specified user. After unloading, the encrypted data corresponding to the user cannot be decrypted and accessed, thereby protecting user data security.

> **NOTE**
>
> This API is currently available only to lock screen applications.

**Required permission**: ohos.permission.STORAGE_MANAGER_CRYPT

**System capability**: SystemCapability.FileManagement.StorageService.Encryption

**System API**: This is a system API.

**Parameters**

  | Name    | Type  | Mandatory| Description|
  | ---------- | ------ | ---- | ---- |
  | userId | number | Yes   | User ID. Value range [100, 10738]. The lock screen application obtains the currently logged-in user of the device and specifies userId as the ID of that user.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified; Or input parameter has type different from the type the interface requires. |
| 13600001 | IPC error. |
| 13600008 | No such object. Possible causes: Cannot find userkey for the specified user. |
| 13600009 | User ID out of range. Possible causes: input parameter userId < 100 or userId > 10736. |

**Example**:

  ```ts
  import { keyManager } from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  let userId: number = 100;
  try {
    keyManager.deactivateUserKey(userId);
    console.info('deactivateUserKey success');
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`deactivateUserKey failed with error. Code: ${error.code}, message: ${error.message}`);
  }
  ```