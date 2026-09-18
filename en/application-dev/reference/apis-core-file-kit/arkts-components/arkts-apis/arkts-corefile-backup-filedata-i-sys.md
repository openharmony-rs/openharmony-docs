# FileData (System API)

Corresponding to a file's data. Filedata is useful when doing IPC with the backup service.

@interface FileData

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## fd

```TypeScript
fd: number
```

Indicates a native file descriptor typically retrieved from the backup service to hold the file's content.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.
