# IncrementalBackupTime (System API)

Save the time information of the incremental backup. IncrementalBackupTime is useful when doing IPC with the backup service.

@interface IncrementalBackupTime

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

Indicates the name of a bundle.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## lastIncrementalTime

```TypeScript
lastIncrementalTime: number
```

Time of the last incremental backup

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.
