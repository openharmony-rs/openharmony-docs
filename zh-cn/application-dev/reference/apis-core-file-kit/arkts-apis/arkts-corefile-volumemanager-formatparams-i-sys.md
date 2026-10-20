# FormatParams（系统接口）

```TypeScript
export interface FormatParams
```

分区格式化的参数。

**起始版本：** 26.0.0

<!--Device-volumeManager-export interface FormatParams--><!--Device-volumeManager-export interface FormatParams-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## fsType

```TypeScript
fsType: string
```

文件系统类型，常见有ext4、vfat和exfat等。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormatParams-fsType: string--><!--Device-FormatParams-fsType: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## quickFormat

```TypeScript
quickFormat?: boolean
```

是否进行快速格式化，默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormatParams-quickFormat?: boolean--><!--Device-FormatParams-quickFormat?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## volumeName

```TypeScript
volumeName?: string
```

格式化后的卷设备名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormatParams-volumeName?: string--><!--Device-FormatParams-volumeName?: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。
