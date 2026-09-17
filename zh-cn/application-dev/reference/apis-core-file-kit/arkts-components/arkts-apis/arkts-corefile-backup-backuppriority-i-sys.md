# BackupPriority（系统接口）

控制备份和恢复的优先级顺序。

@interface BackupPriority

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## priority

```TypeScript
priority?: number
```

应用的优先级，数值越大优先级越高。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。
