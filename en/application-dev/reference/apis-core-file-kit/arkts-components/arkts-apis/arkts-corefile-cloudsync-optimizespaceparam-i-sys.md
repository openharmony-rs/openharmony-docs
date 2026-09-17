# OptimizeSpaceParam (System API)

Sets the total optimization space and aging days.

**Since:** 17

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## agingDays

```TypeScript
agingDays: number
```

Aging days. The system optimizes the local images and videos that have been uploaded to the cloud but not viewed for more than the aging days.

**Type:** number

**Since:** 17

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## totalSize

```TypeScript
totalSize:number
```

Total size of the optimization space. You can obtain the total size of all files to be aged through the media library API. The size is transferred by the application and is in bytes.

**Type:** number

**Since:** 17

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.
