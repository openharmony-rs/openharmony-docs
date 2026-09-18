# SyncFolderAccessor (System API)

A sync root management class that enables the File Manager to access the sync root information registered by third- party cloud disks.

**Since:** 21

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **SyncFolderAccessor** instance.

**Since:** 21

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. application which is not a system application uses system API. |

**Examples**

```TypeScript
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

## getAllSyncFolders

```TypeScript
getAllSyncFolders(): Promise<Array<SyncFolder>>
```

Obtains information about all registered sync roots. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SyncFolder](arkts-corefile-clouddiskmanager-syncfolder-i-sys.md)&gt;&gt; | Promise that returns the sync root list of all cloud disk applications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Device not supported. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc-failed) | IPC communication failed. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure. Retry is recommended (e.g., network issues). |
| [34400015](../errorcode-clouddiskmanager-sys.md#34400015-cloud-disk-not-allowed) | Cloud disk is not allowed on this device. |

**Examples**

```TypeScript
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
