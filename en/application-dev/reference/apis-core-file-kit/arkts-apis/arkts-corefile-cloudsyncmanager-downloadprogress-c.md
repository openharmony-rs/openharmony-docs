# DownloadProgress

Describes the full download progress.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## downloadedSize

```TypeScript
downloadedSize: number
```

Size of the downloaded data, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, **INT64_MAX** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## failedCount

```TypeScript
failedCount: number
```

Number of files that fail to be downloaded. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## state

```TypeScript
state: DownloadState
```

Download state.

**Type:** [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## stopReason

```TypeScript
stopReason: DownloadStopReason
```

Reason why the download stops.

**Type:** [DownloadStopReason](arkts-corefile-cloudsyncmanager-downloadstopreason-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## successfulCount

```TypeScript
successfulCount: number
```

Number of downloaded files. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalCount

```TypeScript
totalCount: number
```

Total number of files to be downloaded. The value range is [0, INT32_MAX]. If the progress is abnormal, **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalSize

```TypeScript
totalSize: number
```

Total size of the files to be downloaded, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, **INT64_MAX** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager
