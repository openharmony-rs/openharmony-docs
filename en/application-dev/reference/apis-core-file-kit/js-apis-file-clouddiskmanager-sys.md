# @ohos.file.cloudDiskManager (Cloud Disk Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=f2a3e6a5e469e2c40ff1e2bbef5e79f03ed357f1 translatedAt=2026-11-10T05:08:14.346Z pushedAt=2026-11-10T07:34:31.150Z nl=1 -->

This module provides the system file management application with the capability to obtain the sync root information (including path, bundle name, and status) registered by third-party cloud drives, and is applicable to scenarios where the sync roots of third-party cloud drives are displayed and managed. A sync root refers to the root path of the local sync directory registered by a third-party cloud drive application in the system. The system file management application can identify and manage the sync status of different cloud drives based on this information.


> **NOTE**
>
> - The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## SyncFolderAccessor

Sync folder accessor, which provides the system file management application with the capability to obtain the list of all registered sync roots (including detailed information such as path, bundle name, and status).

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

### constructor

constructor()

Constructor of SyncFolderAccessor, used to create an instance of the SyncFolderAccessor class.

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
  import { cloudDiskManager } from '@kit.CoreFileKit';
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

Obtains the information of all registered sync roots. This API is applicable to scenarios where the system file management application displays and manages the list of third-party cloud disk sync roots. This API uses an asynchronous callback.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**Return value**

| Type| Description|
| --- | -- |
| Promise&lt;Array&lt;[SyncFolder](#syncfolder)&gt;&gt; | Promise object. When resolved, returns the list of sync roots of all third-party cloud disk applications; when rejected, returns a BusinessError error object. |

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended (e.g., network issues). |
| 34400015  | Cloud disk is not allowed on this device.|

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
const TAG: string = '[cloudDiskManager]';

try {
    console.info(`${TAG}getAllSyncFolders start`);
    let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
    syncFolderAccessor.getAllSyncFolders().then((syncFolders) => {
        console.info(`${TAG}getAllSyncFolders success, length: ${syncFolders.length}`);
        for (let i = 0; i < syncFolders.length; ++i) {
            console.info(`${TAG}syncFolders[${i}].path: ${syncFolders[i].path}`);
            console.info(`${TAG}syncFolders[${i}].bundleName: ${syncFolders[i].bundleName}`);
            console.info(`${TAG}syncFolders[${i}].state: ${syncFolders[i].state}`);
            if (syncFolders[i].displayNameResId) {
                console.info(`${TAG}syncFolders[${i}].displayNameResId: ${syncFolders[i].displayNameResId}`);
            }
            if (syncFolders[i].customAlias) {
                console.info(`${TAG}syncFolders[${i}].customAlias: ${syncFolders[i].customAlias}`);
            }
        }
    }).catch((err: BusinessError<object>) => {
        console.error(`${TAG}Failed to getAllSyncFolders. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`${TAG}getAllSyncFolders failed. Code: ${error.code}, message: ${error.message}`);
}
```

## SyncFolder

Represents sync root information, including the path, bundle name, state, and display alias of the sync root. It is used by the system file management application to identify and manage sync roots of different cloud disks.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Type  | Read-Only| Optional| Description     |
| --------- | ------ | ---- | ---- | ---------------------------- |
| path | string | No | No | Local absolute path corresponding to the sync root, indicating the root path of the local sync directory registered by the third-party cloud disk application in the system. |
| bundleName | string | No | No | Bundle name of the third-party cloud disk application that registers the sync root. |
| state | [SyncFolderState](#syncfolderstate) | No | No | Sync state of the sync root. The value is INACTIVE or ACTIVE. For details, see SyncFolderState. |
| displayNameResId | number | No | Yes | Resource ID used to map the alias displayed in the file management application list. When the third-party cloud disk application specifies the display alias through a resource ID, this field contains the corresponding resource ID. If not specified, the default value is undefined, indicating that the alias specified by the resource ID is not used. Both this field and customAlias can be used to set the display alias. When both exist, the system implementation prevails. |
| customAlias | string | No | Yes | Custom alias displayed in the file management application list. When the third-party cloud disk application directly specifies a custom alias, this field contains the corresponding alias content. If not specified, the default value is undefined. Both this field and displayNameResId can be used to set the display alias. When both exist, the system implementation prevails. |

## SyncFolderState

Enumerates the states of a third-party cloud disk sync root.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | The sync root is inactive.|
| ACTIVE    |  1   | The sync root is active. |
