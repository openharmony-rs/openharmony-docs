# @ohos.file.cloudDiskManager (Cloud Disk Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

This module enables the File Manager to obtain the sync root information registered by third-party cloud disks. A sync root is the root path of the local sync directory registered by a third-party cloud disk application in the system. The File Manager can use this information to identify and manage the sync status of different cloud disks.

In addition, this module enables the File Manager to hydrate and dehydrate placeholder files of third-party cloud disks and subscribe to hydration progress. It is applicable to scenarios such as opening cloud files online and optimizing local storage space. A placeholder file is a file created by a third-party cloud disk application within the sync root. Only the file metadata and placeholder data are retained on the local device, and the file content is stored in the cloud. Hydration downloads the cloud content to the local device so that the file can be accessed as usual, and dehydration reverts a fully hydrated file to a placeholder, releasing local storage space while retaining the logical size of the file.

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
| 34400015  | Cloud disk is not allowed on this device.|

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

## CloudDiskSystemAccessor<sup>26+</sup>

Cloud disk system accessor that enables the File Manager to hydrate and dehydrate placeholder files of third-party cloud disks, and subscribe to hydration progress. Before use, you must create a **CloudDiskSystemAccessor** instance.

**Since**: 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

### constructor<sup>26+</sup>

constructor()

A constructor used to create a **CloudDiskSystemAccessor** instance.

**Since**: 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 34400014 | Temporary failure. Retry is recommended. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
  console.info('CloudDiskSystemAccessor created successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`CloudDiskSystemAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
}
```

### onHydrateProgress<sup>26+</sup>

onHydrateProgress(callback: Callback&lt;[HydrateProgress](#hydrateprogress26)&gt;): void

Subscribes to progress events of hydration and cancellation operations invoked on this instance. This API is applicable to the scenario where the File Manager displays the hydration progress of files. The callback is selected by the calling instance, regardless of the target file. Only one callback can be registered for this instance at a time. Repeated subscriptions with valid arguments retain the existing callback without reporting a duplicate-registration error. Subscribing after a task starts, or subscribing again after calling [offHydrateProgress](#offhydrateprogress26), receives subsequent events routed to this instance. Earlier events are not replayed. An instance can start multiple hydration tasks at the same time, and files are distinguished by **filePath** in [HydrateProgress](#hydrateprogress26).

**Since**: 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress26)&gt; | Yes| Callback invoked when the progress of a hydration task started by this instance changes.|

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400008 | The sync root path is not registered. |
| 34400014 | Temporary failure. Retry is recommended. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();

let callback = (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
};

try {
  accessor.onHydrateProgress(callback);
  console.info('subscribe hydrateProgress successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`onHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### offHydrateProgress<sup>26+</sup>

offHydrateProgress(callback?: Callback&lt;[HydrateProgress](#hydrateprogress26)&gt;): void

Unsubscribes this instance from hydration progress events. This operation does not cancel the hydration tasks started by this instance, and subscriptions registered by other instances are not affected. If no callback is registered on the current instance, this API succeeds after permission and parameter checks.

**Since**: 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress26)&gt; | No| Callback to be unregistered. The hydration progress callback registered on the current instance is unsubscribed regardless of this parameter.|

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400008 | The sync root path is not registered. |
| 34400014 | Temporary failure. Retry is recommended. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();

let callback = (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
};

accessor.onHydrateProgress(callback);

try {
  accessor.offHydrateProgress(callback); // Unsubscribe from the specified callback.
  accessor.offHydrateProgress(); // Unsubscribe from all callbacks.
  console.info('unsubscribe hydrateProgress successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`offHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### hydratePlaceholder<sup>26+</sup>

hydratePlaceholder(filePath: string, callbackType: [CallbackType](#callbacktype26), priority: [HydratePriority](#hydratepriority26)): Promise&lt;void&gt;

Starts or cancels hydration of a placeholder file. This API is applicable to the scenario where the File Manager opens a placeholder file of a third-party cloud disk online. This API uses a promise to return the result.

> **NOTE**
>
> - If **callbackType** is **FETCH_DATA**, hydration starts. The promise is fulfilled once the hydration task is created and queued. This only indicates that the task has been created, not that the file has started downloading or the hydration is complete. The hydration progress is delivered to the [onHydrateProgress](#onhydrateprogress26) callback of the instance that starts the task, and a callback does not have to be registered before starting or cancelling a task. The file hydration state changes from PENDING and IN_PROGRESS to the final state COMPLETED or CANCELLED.
> - If **callbackType** is **CANCEL_FETCH_DATA**, hydration is cancelled. If an in-progress hydration task exists for the target file, the task is cancelled, and the CANCELLED event is delivered only to the instance that requests the cancellation, even if the task was started by another instance. If no in-progress hydration task exists, the promise is rejected with error code 34400032. If the cancelling instance has no registered callback, its cancellation event is not delivered to another instance or replayed later. Automatic cancellation by the service is routed to the instance that started the task.
> - The number of pending (queued) hydration tasks is limited (20 for a single cloud disk application and 40 globally). When the limit is reached, the promise is rejected with error code 34400034. In this case, wait for some hydration tasks to complete or be cancelled, and then try again. In addition, a maximum of five hydration tasks of a single cloud disk application and ten hydration tasks globally can run at the same time, and excess tasks wait in the queue without an error being reported.

**Since**: 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| filePath | string | Yes| Path of the placeholder file. The value must be an absolute path prefixed with "/storage/Users/currentUser/" and within the registered sync root directory of a third-party cloud disk application.|
| callbackType | [CallbackType](#callbacktype26) | Yes| Callback type. The value **FETCH_DATA** starts hydration, and the value **CANCEL_FETCH_DATA** cancels hydration. The value **DEHYDRATE** is not supported by this API and results in error code 34400001.|
| priority | [HydratePriority](#hydratepriority26) | Yes| Priority of the hydration task. This parameter takes effect only when **callbackType** is **FETCH_DATA**.|

**Return value**

| Type| Description|
| ---- | ---- |
| Promise&lt;void&gt; | Promise that returns no value. When hydration starts, the promise is fulfilled after the hydration task is created. When hydration is cancelled, the promise is fulfilled after the cancellation request is accepted.|

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400008 | The sync root path is not registered. |
| 34400010 | The sync root path does not exist. |
| 34400014 | Temporary failure. Retry is recommended. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | Hydration in progress. |
| 34400021 | The callback table is not registered. |
| 34400023 | The parent directory of the target path is not a directory. |
| 34400024 | The target path does not exist. |
| 34400025 | The file name or path is too long. |
| 34400031 | The placeholder file is already fully hydrated. |
| 34400032 | No hydration task is in progress for the target file. |
| 34400033 | The stored placeholder state is invalid. |
| 34400034 | The number of active placeholder hydration tasks has reached the limit. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.onHydrateProgress((progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
});

accessor.hydratePlaceholder(filePath, cloudDiskManager.CallbackType.FETCH_DATA,
  cloudDiskManager.HydratePriority.HIGH).then(() => {
  console.info('hydrate task created successfully');
}).catch((err: BusinessError) => {
  console.error(`hydratePlaceholder failed with error message: ${err.message}, error code: ${err.code}`);
});
```

### dehydrateFile<sup>26+</sup>

dehydrateFile(filePath: string): Promise&lt;void&gt;

Dehydrates a fully hydrated placeholder file, reverting it to an unhydrated placeholder to release local storage space. This API is applicable to the storage space optimization scenario of the File Manager. The file can have been hydrated by another instance, and this operation does not emit hydration progress events. This API uses a promise to return the result.

> **NOTE**
>
> - Before dehydration, the system sends a dehydration authorization request to the third-party cloud disk application. If the application denies the authorization, the promise is rejected with error code 34400029, and the file remains unchanged.
> - Calling this API on a file that is already unhydrated is an idempotent operation, and the promise is fulfilled.
> - Dehydration is not allowed when an in-progress hydration task exists for the file. In this case, the promise is rejected with error code 34400019.

**Since**: 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| filePath | string | Yes| Path of the placeholder file to dehydrate. The value must be an absolute path prefixed with "/storage/Users/currentUser/" and within the registered sync root directory of a third-party cloud disk application.|

**Return value**

| Type| Description|
| ---- | ---- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400008 | The sync root path is not registered. |
| 34400010 | The sync root path does not exist. |
| 34400014 | Temporary failure. Retry is recommended. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | Hydration in progress. |
| 34400020 | The available disk space is insufficient. |
| 34400021 | The callback table is not registered. |
| 34400023 | The parent directory of the target path is not a directory. |
| 34400024 | The target path does not exist. |
| 34400025 | The file name or path is too long. |
| 34400029 | The application denied placeholder dehydration. |
| 34400033 | The stored placeholder state is invalid. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.dehydrateFile(filePath).then(() => {
  console.info('dehydrate file successfully');
}).catch((err: BusinessError) => {
  console.error(`dehydrateFile failed with error message: ${err.message}, error code: ${err.code}`);
});
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

## HydrateProgress<sup>26+</sup>

Describes the progress of a hydration task, which is reported by the callback subscribed via [onHydrateProgress](#onhydrateprogress26).

**Since**: 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Type  | Read-Only| Optional| Description     |
| --------- | ------ | ---- | ---- | ---------------------------- |
| filePath | string | No  | No  | Original absolute path of the file, consistent with the one passed in to hydratePlaceholder.    |
| state   | [HydrateProgressState](#hydrateprogressstate26) | No  | No  | Hydration progress state.  |
| processedSize   | long | No  | No  | Number of bytes hydrated. This field is valid only when **state** is IN_PROGRESS. The unit is byte.  |
| totalSize   | long | No  | No  | Total size of the file being hydrated, in bytes.  |

## HydrateProgressState<sup>26+</sup>

Enumerates the states of the hydration progress.

**Since**: 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| PENDING  |  0   | The hydration task has been created but has not started.|
| IN_PROGRESS    |  1   | The hydration is in progress.  |
| COMPLETED    |  2   | The hydration is complete.  |
| CANCELLED    |  3   | The hydration is cancelled due to user cancellation, the cloud disk application giving up the task, task timeout, or internal system termination.  |

## CallbackType<sup>26+</sup>

Enumerates the callback types of cloud file data fetching and dehydration authorization.

**Since**: 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| FETCH_DATA  |  0   | Fetches cloud file data (starts hydration).|
| CANCEL_FETCH_DATA    |  1   | Cancels fetching cloud file data (cancels hydration).  |
| DEHYDRATE    |  2   | Dehydration authorization request. Before dehydration, the system sends a dehydration authorization request to the third-party cloud disk application that has registered callbacks, and the application determines whether to allow the dehydration.  |

## HydratePriority<sup>26+</sup>

Enumerates the priorities of hydration tasks.

**Since**: 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| LOW  |  0   | Low priority.|
| NORMAL    |  1   | Normal priority.  |
| HIGH    |  2   | High priority.  |
