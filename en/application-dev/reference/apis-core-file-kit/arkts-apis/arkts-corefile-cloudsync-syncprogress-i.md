# SyncProgress

```TypeScript
interface SyncProgress
```

Represents information about the device-cloud sync progress.

**Since:** 12

<!--Device-cloudSync-interface SyncProgress--><!--Device-cloudSync-interface SyncProgress-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: ErrorType
```

Sync error.

**Type:** [ErrorType](arkts-corefile-cloudsync-errortype-e.md)

**Since:** 12

<!--Device-SyncProgress-error: ErrorType--><!--Device-SyncProgress-error: ErrorType-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: SyncState
```

Device-cloud sync state.

**Type:** [SyncState](arkts-corefile-cloudsync-syncstate-e.md)

**Since:** 12

<!--Device-SyncProgress-state: SyncState--><!--Device-SyncProgress-state: SyncState-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
