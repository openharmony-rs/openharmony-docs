# CloudFileInfo

Represents the number and size of local and cloud files of an application.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## bothFileCount

```TypeScript
bothFileCount: number
```

Total number of local files that have been uploaded to the cloud. The value range is [0, INT32_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## bothFileTotalSize

```TypeScript
bothFileTotalSize: number
```

Total size of local files that have been uploaded to the cloud, in bytes. The value range is [0, INT64_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## cloudFileCount

```TypeScript
cloudFileCount: number
```

Total number of cloud files that are not downloaded locally. The value range is [0, INT32_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## cloudFileTotalSize

```TypeScript
cloudFileTotalSize: number
```

Total size of cloud files that are not downloaded locally, in bytes. The value range is [0, INT64_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## localFileCount

```TypeScript
localFileCount: number
```

Total number of local files that are not uploaded to the cloud. The value range is [0, INT32_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## localFileTotalSize

```TypeScript
localFileTotalSize: number
```

Total size of local files that are not uploaded to the cloud, in bytes. The value range is [0, INT64_MAX].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager
