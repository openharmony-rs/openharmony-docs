# OptimizeSpaceProgress (System API)

Represents the space optimization states and optimization progress.

**Since:** 17

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## progress

```TypeScript
progress: number
```

Optimization progress percentage. The value range is [0, 100].

**Type:** number

**Since:** 17

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## state

```TypeScript
state: OptimizeState
```

Enumerates the space optimization states.

**Type:** [OptimizeState](arkts-corefile-cloudsync-optimizestate-e-sys.md)

**Since:** 17

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.
