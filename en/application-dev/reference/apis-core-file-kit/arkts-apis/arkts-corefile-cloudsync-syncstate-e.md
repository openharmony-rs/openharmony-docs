# SyncState

```TypeScript
enum SyncState
```

Enumerates the device-cloud sync states.

> **NOTE:** 
> 
> If a sync progress event listener is registered for an application, a callback will be invoked to notify the
> application when the device-cloud sync state is changed.

**Since:** 12

<!--Device-cloudSync-enum SyncState--><!--Device-cloudSync-enum SyncState-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## COMPLETED

```TypeScript
COMPLETED = 4
```

Sync completed.

**Since:** 12

<!--Device-SyncState-COMPLETED = 4--><!--Device-SyncState-COMPLETED = 4-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOAD_FAILED

```TypeScript
DOWNLOAD_FAILED = 3
```

Download failed.

**Since:** 12

<!--Device-SyncState-DOWNLOAD_FAILED = 3--><!--Device-SyncState-DOWNLOAD_FAILED = 3-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOADING

```TypeScript
DOWNLOADING = 2
```

The file is being downloaded.

**Since:** 12

<!--Device-SyncState-DOWNLOADING = 2--><!--Device-SyncState-DOWNLOADING = 2-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## STOPPED

```TypeScript
STOPPED = 5
```

Sync stopped.

**Since:** 12

<!--Device-SyncState-STOPPED = 5--><!--Device-SyncState-STOPPED = 5-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOAD_FAILED

```TypeScript
UPLOAD_FAILED = 1
```

Upload failed.

**Since:** 12

<!--Device-SyncState-UPLOAD_FAILED = 1--><!--Device-SyncState-UPLOAD_FAILED = 1-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOADING

```TypeScript
UPLOADING = 0
```

The file is being uploaded.

**Since:** 12

<!--Device-SyncState-UPLOADING = 0--><!--Device-SyncState-UPLOADING = 0-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
