# IncrementalBackupData (System API)

Corresponds to an incremental application, including its last incremental time and incremental list.

@extends IncrementalBackupTime, FileManifestData, BackupParams, BackupPriority @interface IncrementalBackupData

**Inheritance/Implementation:** IncrementalBackupData extends [IncrementalBackupTime](arkts-corefile-backup-incrementalbackuptime-i-sys.md)<!--Del-->, [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md)<!--DelEnd--><!--Del-->, [BackupParams](arkts-corefile-backup-backupparams-i-sys.md)<!--DelEnd--><!--Del-->, [BackupPriority](arkts-corefile-backup-backuppriority-i-sys.md)<!--DelEnd-->

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```
