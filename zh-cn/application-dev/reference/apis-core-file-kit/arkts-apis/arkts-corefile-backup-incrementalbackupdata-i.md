# IncrementalBackupData（系统接口）

一次增量备份对象，包含最后一次增量备份时间和增量清单。

**继承/实现关系：** IncrementalBackupData extends [IncrementalBackupTime](arkts-corefile-backup-incrementalbackuptime-i-sys.md), [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md), [BackupParams](arkts-corefile-backup-backupparams-i-sys.md), [BackupPriority](arkts-corefile-backup-backuppriority-i-sys.md)

**起始版本：** 12

<!--Device-backup-interface IncrementalBackupData extends IncrementalBackupTime, FileManifestData, BackupParams, BackupPriority--><!--Device-backup-interface IncrementalBackupData extends IncrementalBackupTime, FileManifestData, BackupParams, BackupPriority-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

