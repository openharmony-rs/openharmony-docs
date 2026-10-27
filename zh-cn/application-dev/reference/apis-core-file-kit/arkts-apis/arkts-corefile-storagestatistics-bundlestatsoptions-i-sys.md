# BundleStatsOptions（系统接口）

```TypeScript
export interface BundleStatsOptions
```

获取应用存储空间信息的选项。

**起始版本：** 26.0.1

<!--Device-storageStatistics-export interface BundleStatsOptions--><!--Device-storageStatistics-export interface BundleStatsOptions-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## index

```TypeScript
index?: number
```

分身应用的索引号，取值范围为大于等于0的整数，默认值为0（表示未分身的主应用）。传入不满足范围的值时返回错误码401。分身应用索引号在分身创建时默认占用从1开始且当前未被占用的最小索引号，并赋值给该应用的[BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md)的appIndex属性，后续可以通过调用[getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md)接口获得。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStatsOptions-index?: int--><!--Device-BundleStatsOptions-index?: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## statFlag

```TypeScript
statFlag?: GetBundleStatsFlag
```

应用存储空间统计信息的标志，用于指定统计范围。默认值是GET_BUNDLE_WITH_ALL_SIZE。

**类型：** [GetBundleStatsFlag](arkts-corefile-storagestatistics-getbundlestatsflag-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStatsOptions-statFlag?: GetBundleStatsFlag--><!--Device-BundleStatsOptions-statFlag?: GetBundleStatsFlag-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。
