# File (System API)

Corresponds to a file, including its metadata and data and the file's manifest data. Files are useful as IPC and backup services.

@extends FileMeta, FileData, FileManifestData @interface File

**Inheritance/Implementation:** File extends [FileMeta](arkts-corefile-backup-filemeta-i-sys.md)<!--Del-->, [FileData](arkts-corefile-backup-filedata-i-sys.md)<!--DelEnd--><!--Del-->, [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md)<!--DelEnd-->

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```
