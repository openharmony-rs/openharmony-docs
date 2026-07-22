# IncrementalBackupTime（系统接口）

记录最后一次增量备份时间，用于描述备份增量的时间点。

**起始版本：** 12

<!--Device-backup-interface IncrementalBackupTime--><!--Device-backup-interface IncrementalBackupTime-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用名称。

**类型：** string

**起始版本：** 12

<!--Device-IncrementalBackupTime-bundleName: string--><!--Device-IncrementalBackupTime-bundleName: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## lastIncrementalTime

```TypeScript
lastIncrementalTime: number
```

最后一次增量备份时间。

**类型：** number

**起始版本：** 12

<!--Device-IncrementalBackupTime-lastIncrementalTime: long--><!--Device-IncrementalBackupTime-lastIncrementalTime: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

