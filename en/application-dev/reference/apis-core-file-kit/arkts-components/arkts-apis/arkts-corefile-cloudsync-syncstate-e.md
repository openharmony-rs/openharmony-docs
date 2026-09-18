# SyncState

Enumerates the device-cloud sync states.

> **NOTE:** 
> 
> If a sync progress event listener is registered for an application, a callback will be invoked to notify the
> application when the device-cloud sync state is changed.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOADING

```TypeScript
UPLOADING = 0
```

The file is being uploaded.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOAD_FAILED

```TypeScript
UPLOAD_FAILED = 1
```

Upload failed.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOADING

```TypeScript
DOWNLOADING = 2
```

The file is being downloaded.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOAD_FAILED

```TypeScript
DOWNLOAD_FAILED = 3
```

Download failed.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## COMPLETED

```TypeScript
COMPLETED = 4
```

Sync completed.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## STOPPED

```TypeScript
STOPPED = 5
```

Sync stopped.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
