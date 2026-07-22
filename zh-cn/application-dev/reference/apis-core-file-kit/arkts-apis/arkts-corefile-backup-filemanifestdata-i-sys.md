# FileManifestData（系统接口）

增量数据中的清单文件信息，用于描述应用增量备份、恢复时对应文件的基础信息。

**起始版本：** 12

<!--Device-backup-interface FileManifestData--><!--Device-backup-interface FileManifestData-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## manifestFd

```TypeScript
manifestFd: number
```

清单文件的文件描述符，通过备份服务获取。

**类型：** number

**起始版本：** 12

<!--Device-FileManifestData-manifestFd: int--><!--Device-FileManifestData-manifestFd: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

