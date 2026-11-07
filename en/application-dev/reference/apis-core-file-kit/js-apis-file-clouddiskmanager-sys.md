# @ohos.file.cloudDiskManager (Cloud Disk Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1b82780d82b04c978a2721a6c816b2f22a388948 translatedAt=2026-11-04T04:02:58.252Z pushedAt=2026-11-04T10:12:33.454Z nl=1 -->

This module provides the system file management application with the capability to obtain sync root information (including path, package name, status, and so on) registered by third-party cloud disks, and is applicable to scenarios of displaying and managing third-party cloud disk sync root directories. A sync root refers to the root path of the local sync directory registered by a third-party cloud disk application in the system. The system file management application can identify and manage the sync status of different cloud disks through this information. This module also supports the system file management application in hydrating and dehydrating placeholder files of third-party cloud disks and subscribing to hydration progress, and is applicable to scenarios such as opening cloud disk files online and optimizing local storage space. A placeholder file is a file created by a third-party cloud disk application within a sync root. Only file metadata and placeholder data are retained locally, while the file content is stored on the cloud side. Hydration refers to downloading cloud-side content to the local device so that the file can be accessed normally. Dehydration refers to reverting a fully hydrated file to a placeholder, releasing local storage space while retaining the logical size of the file.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## SyncFolderAccessor

Sync folder accessor, which provides the system file management application with the capability to obtain the list of all registered sync roots (including detailed information such as path, package name, and status).

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

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
            if (syncFolders[i].isSupportPlaceHolder) {
                console.info(`${TAG}syncFolders[${i}].isSupportPlaceHolder: ${syncFolders[i].isSupportPlaceHolder}`);
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

## CloudDiskSystemAccessor

The cloud disk system accessor provides the system file management application with the capability to hydrate and dehydrate placeholder files of third-party cloud disks, and supports subscribing to hydration progress. Before use, you need to create a CloudDiskSystemAccessor instance.

**Since:** 26.0.1

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

### constructor

constructor()

The constructor of CloudDiskSystemAccessor, used to create an instance of the CloudDiskSystemAccessor class.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 34400014 | Temporary failure. Failed to initialize the native accessor instance. Please try again. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
  console.info('CloudDiskSystemAccessor created successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`CloudDiskSystemAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
}
```

### onHydrateProgress

onHydrateProgress(callback: Callback&lt;HydrateProgress&gt;): void

Subscribes to the progress events of hydration and cancellation operations initiated by this instance. This API is applicable to scenarios where a file management application displays the file hydration progress. It uses an asynchronous callback.

> **NOTE**
>
> - The callback is routed by the instance that initiates the operation and is unrelated to the target file. The same instance can initiate multiple hydration tasks at the same time, and different files are distinguished by the filePath field in [HydrateProgress](#hydrateprogress).
> - Only one callback can be registered for the same instance at a time. When a valid parameter is passed for repeated subscription, the existing callback is retained and no duplicate registration error is reported.
> - If you subscribe after a task is initiated, or subscribe again after unsubscribing by calling [offHydrateProgress](#offhydrateprogress)(), only subsequent events routed to this instance can be received, and previous progress events are not replayed.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress)&gt; | Yes | Callback used to notify the application when the hydration task progress or status changes. |

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400014 | Temporary failure. Failed to initialize the callback, resolve the user account, or complete an internal operation. Please try again. |

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
  console.info('subscribe hydrateProgress successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`onHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### offHydrateProgress

offHydrateProgress(callback?: Callback&lt;HydrateProgress&gt;): void

Unsubscribes from the hydration progress events of this instance. This API uses an asynchronous callback.

> **NOTE**
>
> - This operation does not cancel the hydration tasks already initiated by this instance, and subscriptions registered by other instances are not affected.
> - If no callback is registered for the current instance, this API returns normally after passing the permission and parameter verification.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress)&gt; | No | Callback function, which cancels the hydration progress callback registered for the current instance. The effect is the same when it is not passed in. |

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried when unregistering this instance's callback from the service. |
| 34400014 | Temporary failure while unregistering the callback. Please try again. |

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
  accessor.offHydrateProgress(callback); // Cancel the specified callback.
  accessor.offHydrateProgress(); // Cancel all callbacks.
  console.info('unsubscribe hydrateProgress successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`offHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### hydratePlaceholder

hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise&lt;void&gt;

Initiates or cancels hydration for a placeholder file. This API applies to the scenario where the file management application opens a third-party cloud disk placeholder file online. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - When callbackType is FETCH_DATA, hydration is initiated: after the task is created successfully, the Promise is fulfilled immediately, which only indicates that the hydration task has been created and enqueued, not that the file has started downloading or that hydration is complete. The hydration progress is delivered through the [onHydrateProgress](#onhydrateprogress)() callback of the instance that initiated the task. It is not necessary to register the callback before initiating or canceling a hydration task. The file hydration state passes through PENDING and IN_PROGRESS in sequence, and finally becomes COMPLETED or CANCELLED.
> - When callbackType is CANCEL_FETCH_DATA, hydration is canceled: if the target file has an in-progress hydration task, it is canceled. Upon successful cancellation, the CANCELLED event is delivered only to the instance that initiated the cancellation (even if the hydration task was initiated by another instance). If no in-progress hydration task exists, the Promise is rejected and error code 34400032 is returned. If the instance that initiated the cancellation has not registered a callback, its cancellation event is not forwarded to other instances, nor is it replayed afterward.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| filePath | string | Yes | Path of the placeholder file. It must be an absolute path prefixed with "/storage/Users/currentUser/", located within the sync root directory registered by the third-party cloud disk application. The maximum length is 4096 and it cannot be empty. |
| callbackType | [CallbackType](#callbacktype) | Yes | Callback type. FETCH_DATA initiates hydration, and CANCEL_FETCH_DATA cancels hydration. DEHYDRATE does not apply to this API, and error code 34400001 is returned if it is passed in. |
| priority | [HydratePriority](#hydratepriority) | Yes | Priority of the hydration task. It takes effect only when callbackType is FETCH_DATA. |

**Return value**

| Type                  | Description             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path, callback type, or file metadata. CallbackType.DEHYDRATE is not supported by this operation. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| 34400014 | Temporary failure. Failed to resolve the user account, access the file, prepare a hydrate task, schedule the request, or complete an internal operation. Please try again. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | A hydrate task for the target file is already pending or in progress. |
| 34400021 | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| 34400023 | A path component that must be a directory is not a directory. |
| 34400024 | A required file or directory does not exist while resolving or accessing the target path. |
| 34400025 | The file name or path is too long. |
| 34400031 | The placeholder is already fully hydrated. |
| 34400032 | Cancellation was requested, but no hydrate task is pending or in progress. |
| 34400033 | The placeholder state or its stored attribute is invalid. |
| 34400034 | The limit on pending hydrate tasks has been reached. |

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
  console.info('hydrate task created successfully.');
}).catch((err: BusinessError) => {
  console.error(`hydratePlaceholder failed with error message: ${err.message}, error code: ${err.code}`);
});
```

### dehydrateFile

dehydrateFile(filePath: string): Promise&lt;void&gt;

Dehydrates a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The file to be dehydrated can be a file hydrated by another instance. This operation does not trigger a hydration progress event.
> - Before dehydration, the system sends a dehydration authorization request to the third-party cloud disk application. If the cloud disk application rejects the authorization, the Promise is rejected and error code 34400029 is returned, and the file remains unchanged.
> - Calling this API when the file is already in the non-hydrated state is an idempotent operation, and the Promise is resolved normally.
> - Dehydration is not allowed when there is an ongoing hydration task for the file. In this case, the Promise is rejected and error code 34400019 is returned.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ACCESS_CLOUD_DISK_INFO

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| filePath | string | Yes | Path of the placeholder file to be dehydrated. It must be an absolute path prefixed with "/storage/Users/currentUser/", located within the sync root range registered by the third-party cloud disk application. The maximum length is 4096 and it cannot be empty. |

**Return value**

| Type                  | Description             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Cloud Disk Management Error Codes](errorcode-clouddiskmanager-sys.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path or a file operation argument, the target is a directory, or the provider request could not be serialized. |
| 34400003 | IPC communication with the service or cloud disk provider failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| 34400014 | Temporary failure. Failed to resolve the user account, access the file, restore its logical size, schedule the request, or complete an internal operation. Please try again. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | A hydrate task for the target file is pending or in progress. |
| 34400020 | The available disk space is insufficient, or the disk quota has been exhausted. |
| 34400021 | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| 34400023 | A path component that must be a directory is not a directory. |
| 34400024 | A required file or directory does not exist while resolving or accessing the target path. |
| 34400025 | The file name or path is too long. |
| 34400029 | The cloud disk provider did not approve the dehydration request. |
| 34400033 | The placeholder state or its stored attribute is invalid. |

**Example**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.dehydrateFile(filePath).then(() => {
  console.info('dehydrate file successfully.');
}).catch((err: BusinessError) => {
  console.error(`dehydrateFile failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## SyncFolder

Represents sync root information, including the path, package name, state, and display alias of the sync root. It is used by the system file management application to identify and manage sync roots of different cloud disks.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Type  | Read-Only| Optional| Description     |
| --------- | ------ | ---- | ---- | ---------------------------- |
| path | string | No | No | Local absolute path corresponding to the sync root, indicating the root path of the local sync directory registered by the third-party cloud disk application in the system. |
| bundleName | string | No | No | Package name of the third-party cloud disk application that registers the sync root. |
| state | [SyncFolderState](#syncfolderstate) | No | No | Sync state of the sync root. The value is INACTIVE or ACTIVE. For details, see SyncFolderState. |
| displayNameResId | number | No | Yes | Resource ID used to map the alias displayed in the file management application list. When the third-party cloud disk application specifies the display alias through a resource ID, this field contains the corresponding resource ID. If not specified, the default value is undefined, indicating that the alias specified by the resource ID is not used. Both this field and customAlias can be used to set the display alias. When both exist, the system implementation prevails. |
| customAlias | string | No | Yes | Custom alias displayed in the file management application list. When the third-party cloud disk application directly specifies a custom alias, this field contains the corresponding alias content. If not specified, the default value is undefined. Both this field and displayNameResId can be used to set the display alias. When both exist, the system implementation prevails. |
| isSupportPlaceHolder | boolean | No | Yes | Whether the sync root supports placeholders. The value true indicates that the sync root supports placeholders, and false indicates that it does not. The default value is false.<br>**Initial Version**: 26.0.1 <br>**Model Constraint**: This API can be used only in the stage model.|

## SyncFolderState

Enumerates the states of a third-party cloud disk sync root.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

| Name     | Value | Description     |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | The sync root is inactive.|
| ACTIVE    |  1   | The sync root is active. |

## HydrateProgress

Describes the progress information of a hydration task, obtained through the callback subscribed by [onHydrateProgress](#onhydrateprogress)().

**Since:** 26.0.1

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

| Name      | Type   | Read-Only | Optional | Description      |
| --------- | ------ | ---- | ---- | ---------------------------- |
| filePath | string | No   | No   | Original absolute path of the file, that is, the filePath passed in when hydratePlaceholder() is called. The maximum length is 4096 and it cannot be empty.     |
| state   | [HydrateProgressState](#hydrateprogressstate) | No   | No   | Hydration progress state.   |
| processedSize   | number | No   | No   | Number of bytes hydrated. It is valid only when state is IN_PROGRESS. The unit is byte.   |
| totalSize   | number | No   | No   | Total size of the file being hydrated, in bytes.   |

## HydrateProgressState

Enumerates the hydration progress states of a hydration task.

**Since:** 26.0.1

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

| Name      | Value  | Description      |
| --------- | -----| ------------------------|
| PENDING  |  0   | The hydration task has been created but has not started processing.|
| IN_PROGRESS    |  1   | Hydration is in progress.  |
| COMPLETED    |  2   | Hydration is complete.  |
| CANCELLED    |  3   | Hydration has been canceled. The cancellation sources include user cancellation and the cloud disk application abandoning the task.  |

## CallbackType

Enumeration of callback types for cloud disk file data retrieval and dehydration authorization.

**Since:** 26.0.1

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

| Name      | Value  | Description      |
| --------- | -----| ------------------------|
| FETCH_DATA  |  0   | Retrieves cloud file data (initiates hydration).|
| CANCEL_FETCH_DATA    |  1   | Cancels retrieval of cloud file data (cancels hydration).  |
| DEHYDRATE    |  2   | Dehydration authorization request. Before dehydration is executed, the system sends a dehydration authorization request to the registered third-party cloud disk application through a callback of this type, and the third-party cloud disk application decides whether to allow this dehydration.  |

## HydratePriority

Enumerates the priorities of hydration tasks.

**Since:** 26.0.1

**System API**: This is a system API.

**System Capability**: SystemCapability.FileManagement.CloudDiskManager

**Model restriction:** This API can be used only in the stage model.

| Name      | Value  | Description      |
| --------- | -----| ------------------------|
| LOW  |  0   | Low priority.|
| NORMAL    |  1   | Normal priority.  |
| HIGH    |  2   | High priority.  |
