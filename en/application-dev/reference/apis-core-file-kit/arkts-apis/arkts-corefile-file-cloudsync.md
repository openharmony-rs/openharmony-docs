# @ohos.file.cloudSync(Device-Cloud Sync)

The **cloudSync** module provides the device-cloud sync capabilities for applications. You can use the APIs to start or stop device-cloud sync and start or stop the download of images.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getCoreFileSyncState](arkts-corefile-cloudsync-getcorefilesyncstate-f.md) | Obtains the upload sync state of a cloud file. This API returns the result synchronously. |
| [registerChange](arkts-corefile-cloudsync-registerchange-f.md) | Subscribes to the change of a file. The callback returns the changed data. |
| [unregisterChange](arkts-corefile-cloudsync-unregisterchange-f.md) | Unsubscribes from the change of a file. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getfilesyncstate) | Obtains the file sync state. This API uses a promise to return the result. |
| [getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getfilesyncstate-1) | Obtains the file sync state. This API uses an asynchronous callback to return the result. |
| [getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getfilesyncstate-2) | Obtains the file sync state. |
| [optimizeStorage](arkts-corefile-cloudsync-optimizestorage-f-sys.md) | Optimizes the resources that have been synced to the cloud from the local Gallery and executes the automatic aging policy according to the remaining local space. This API uses a promise to return the result. |
| [startOptimizeSpace](arkts-corefile-cloudsync-startoptimizespace-f-sys.md) | Optimizes local resources that have been synced to the cloud and optimizes local images and videos that have not been accessed before the aging period expires. This API uses a promise to return the result. The callback returns the optimization progress. |
| [stopOptimizeSpace](arkts-corefile-cloudsync-stopoptimizespace-f-sys.md) | Synchronously stops optimizing cloud resource space. This method is used with **startOptimizeSpace**. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [CloudFileCache](arkts-corefile-cloudsync-cloudfilecache-c.md) | Provides APIs for the file manager application to download files from the Drive Kit to a local device. |
| [FileSync](arkts-corefile-cloudsync-filesync-c.md) | Provides APIs for the file manager application to perform device-cloud sync of the files stored in the Drive Kit. Before using the APIs of this class, you need to create a **FileSync** instance. |
| [FileVersion](arkts-corefile-cloudsync-fileversion-c.md) | Represents the device-cloud file version management class. It allows you to manage historical versions of client- cloud files, obtain the list of historical versions, download historical versions to the local device, replace the current local file with a historical version file, and query and remove conflict flags for version conflicts. |
| [MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md) | Represents the batch download progress of a file from the Drive Kit. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [CloudFileCache](arkts-corefile-cloudsync-cloudfilecache-c-sys.md) | Provides APIs for the file manager application to download files from the Drive Kit to a local device. |
| [Download](arkts-corefile-cloudsync-download-c-sys.md) | Provides APIs for downloading image files to **Gallery**. Before using the APIs of **Download**, you need to create a **Download** instance. |
| [FileSync](arkts-corefile-cloudsync-filesync-c-sys.md) | Provides APIs for the file manager application to perform device-cloud sync of the files stored in the Drive Kit. Before using the APIs of this class, you need to create a **FileSync** instance. |
| [GallerySync](arkts-corefile-cloudsync-gallerysync-c-sys.md) | Provides APIs to implement device-cloud sync of media assets in **Gallery**. Before using the APIs of **GallerySync**, you need to create a **GallerySync** instance. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ChangeData](arkts-corefile-cloudsync-changedata-i.md) | Represents the data change information. |
| [DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md) | Represents information about the download progress of a cloud file. |
| [FailedFileInfo](arkts-corefile-cloudsync-failedfileinfo-i.md) | Represents a list of files that fail to be downloaded from the Drive Kit and failure causes. |
| [HistoryVersion](arkts-corefile-cloudsync-historyversion-i.md) | Represents the historical version information of the device-cloud file when the [gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#gethistoryversionlist) method of the [FileVersion](arkts-corefile-cloudsync-fileversion-c.md) class is called. |
| [SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md) | Represents information about the device-cloud sync progress. |
| [VersionDownloadProgress](arkts-corefile-cloudsync-versiondownloadprogress-i.md) | Represents the download state and progress information of historical version files when the [downloadHistoryVersion](arkts-corefile-cloudsync-fileversion-c.md#downloadhistoryversion) method of the [FileVersion](arkts-corefile-cloudsync-fileversion-c.md) class is called. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [OptimizeSpaceParam](arkts-corefile-cloudsync-optimizespaceparam-i-sys.md) | Sets the total optimization space and aging days. |
| [OptimizeSpaceProgress](arkts-corefile-cloudsync-optimizespaceprogress-i-sys.md) | Represents the space optimization states and optimization progress. |
| [UploadProgress](arkts-corefile-cloudsync-uploadprogress-i-sys.md) | The UploadProgress data structure. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DownloadErrorType](arkts-corefile-cloudsync-downloaderrortype-e.md) | Enumerates the device-cloud download error types. |
| [DownloadFileType](arkts-corefile-cloudsync-downloadfiletype-e.md) | Enumerates the download file types from the Drive Kit. |
| [ErrorType](arkts-corefile-cloudsync-errortype-e.md) | Enumerates the device-cloud sync errors. |
| [FileState](arkts-corefile-cloudsync-filestate-e.md) | Enumerates the device-cloud file sync states. |
| [NotifyType](arkts-corefile-cloudsync-notifytype-e.md) | Enumerates the data change types. |
| [State](arkts-corefile-cloudsync-state-e.md) | Enumerates the download states of a cloud file. |
| [SyncState](arkts-corefile-cloudsync-syncstate-e.md) | Enumerates the device-cloud sync states. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ErrorType](arkts-corefile-cloudsync-errortype-e-sys.md) | Enumerates the device-cloud sync errors. |
| [FileSyncState](arkts-corefile-cloudsync-filesyncstate-e-sys.md) | Enumerates the device-cloud file sync states. |
| [OptimizeState](arkts-corefile-cloudsync-optimizestate-e-sys.md) | Enumerates the space optimization states. |
| [State](arkts-corefile-cloudsync-state-e-sys.md) | Enumerates the download states of a cloud file. |
| [UploadState](arkts-corefile-cloudsync-uploadstate-e-sys.md) | Describes the State type of file upload. |
<!--DelEnd-->
