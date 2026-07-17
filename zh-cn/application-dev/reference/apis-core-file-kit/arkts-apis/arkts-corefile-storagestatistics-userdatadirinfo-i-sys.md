# UserdataDirInfo（系统接口）

用户设备中/data目录下的空间占用详情。

**起始版本：** 23

<!--Device-storageStatistics-export interface UserdataDirInfo--><!--Device-storageStatistics-export interface UserdataDirInfo-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## path

```TypeScript
path: string
```

路径名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserdataDirInfo-path: string--><!--Device-UserdataDirInfo-path: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## totalCnt

```TypeScript
totalCnt: number
```

路径下目录和文件总数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserdataDirInfo-totalCnt: int--><!--Device-UserdataDirInfo-totalCnt: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## totalSize

```TypeScript
totalSize: number
```

路径占用的总空间大小，单位Byte。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserdataDirInfo-totalSize: long--><!--Device-UserdataDirInfo-totalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

