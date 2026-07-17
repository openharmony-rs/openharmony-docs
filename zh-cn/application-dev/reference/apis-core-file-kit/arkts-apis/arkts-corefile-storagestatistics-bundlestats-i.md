# BundleStats

获取捆绑包统计信息。

**起始版本：** 9

<!--Device-storageStatistics-export interface BundleStats--><!--Device-storageStatistics-export interface BundleStats-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## appSize

```TypeScript
appSize: number
```

应用安装文件大小（单位为Byte）。

**类型：** number

**起始版本：** 9

<!--Device-BundleStats-appSize: long--><!--Device-BundleStats-appSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## cacheSize

```TypeScript
cacheSize: number
```

应用缓存文件大小（单位为Byte）。

**类型：** number

**起始版本：** 9

<!--Device-BundleStats-cacheSize: long--><!--Device-BundleStats-cacheSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## dataSize

```TypeScript
dataSize: number
```

应用文件存储大小（除应用安装文件）（单位为Byte）。

**类型：** number

**起始版本：** 9

<!--Device-BundleStats-dataSize: long--><!--Device-BundleStats-dataSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

