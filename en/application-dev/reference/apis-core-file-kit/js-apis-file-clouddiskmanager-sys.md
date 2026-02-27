# @ohos.file.cloudDiskManager (Cloud Disk Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @zhuangzhuang-->
<!--Designer: @wang_zhangjun; @zhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

This module enables the File Manager to obtain the sync root information registered by third-party cloud disks.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## SyncFolderAccessor

A sync root management class that enables the File Manager to access the sync root information registered by third-party cloud disks.

### constructor

constructor()

A constructor used to create a **SyncFolderAccessor** instance.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  @Entry
  @Component
  struct Index {
    build() {
      Column() {
        Button('constructor')
        .onClick(async() => {
            try {
              let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
            } catch (err) {
                let error: BusinessError = err as BusinessError;
                console.error(`SyncFolderAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
            }
        });
      }
    }
  }

  ```
  
### getAllSyncFolders

getAllSyncFolders(): Promise&lt;Array&lt;SyncFolder&gt;&gt;

Obtains information about all registered sync roots. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**Return value**

| Type| Description|
| --- | -- |
| Promise&lt;Array&lt;[SyncFolder](#syncfolder)&gt;&gt; | Promise that returns the sync root list of all cloud disk applications.|

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400014  | Temporary failure, Retry is recommended (e.g., network issues). |
| 34400015  | Cloud disk not allowed on this device.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
const TAG: string = '[cloudDiskManager]';

try {
    console.info(TAG + `getAllSyncFolders start`);
    let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
    syncFolderAccessor.getAllSyncFolders().then((syncFolders) => {
        if (syncFolders) {
            console.info(TAG + `getAllSyncFolders success, length: ${syncFolders.length}`);
            for (let i = 0; i < syncFolders.length; ++i) {
                console.info(TAG + `syncFolders[${i}].path: ${syncFolders[i].path}`);
                console.info(TAG + `syncFolders[${i}].bundleName: ${syncFolders[i].bundleName}`);
                console.info(TAG + `syncFolders[${i}].state: ${syncFolders[i].state}`);
                if (syncFolders[i].displayNameResId) {
                    console.info(TAG + `syncFolders[${i}].displayNameResId: ${syncFolders[i].displayNameResId}`);
                }
                if (syncFolders[i].customAlias) {
                    console.info(TAG + `syncFolders[${i}].customAlias: ${syncFolders[i].customAlias}`);
                }
            }
        } else {
            console.info(TAG + `getAllSyncFolders failed`);
        }
    }).catch((e: BusinessError<object>) => {
        console.error(TAG + `getAllSyncFolders then catch err, code: ${e.code}, message: ${e.message}`);
    })
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(TAG + `getAllSyncFolders failed. code: ${error.code}, message: ${error.message}`);
}
```

## SyncFolder

Encapsulates the sync root information.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Type  | Read-Only| Optional| Description     |
| --------- | ------ | ---- | ---- | ---------------------------- |
| path | string | No  | No  | URI of the sync root.    |
| bundleName   | string | No  | No  | Bundle name of the sync root.  |
| state   | [SyncFolderState](#syncfolderstate) | No  | No  | State of the sync root.  |
| displayNameResId   | number | No  | Yes  | Resource ID, which can be mapped to the alias displayed in the File Manager list. The default value is **undefined**.  |
| customAlias   | string | No  | Yes  | Custom alias displayed in the File Manager list. The default value is **undefined**.  |

## SyncFolderState

Enumerates the states of the sync root.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | The sync root is inactive.|
| ACTIVE    |  1   | The sync root is active. |
