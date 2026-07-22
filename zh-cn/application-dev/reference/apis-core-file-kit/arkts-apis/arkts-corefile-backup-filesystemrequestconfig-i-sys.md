# FileSystemRequestConfig（系统接口）

配置系统执行碎片清理所需的参数。

**起始版本：** 23

<!--Device-backup-interface FileSystemRequestConfig--><!--Device-backup-interface FileSystemRequestConfig-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## triggerType

```TypeScript
triggerType: number
```

指定碎片清理的触发类型，取值0表示执行存储器件碎片清理。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSystemRequestConfig-triggerType: int--><!--Device-FileSystemRequestConfig-triggerType: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## waitTime

```TypeScript
waitTime: number
```

执行碎片清理的最大允许时间，单位为秒，取值范围为0至300。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSystemRequestConfig-waitTime: int--><!--Device-FileSystemRequestConfig-waitTime: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## writeSize

```TypeScript
writeSize: number
```

碎片清理的目标大小，单位为MB，取值范围为0至2097152。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSystemRequestConfig-writeSize: int--><!--Device-FileSystemRequestConfig-writeSize: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

