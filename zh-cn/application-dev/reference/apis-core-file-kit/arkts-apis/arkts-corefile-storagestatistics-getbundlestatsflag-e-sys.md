# GetBundleStatsFlag（系统接口）

```TypeScript
export enum GetBundleStatsFlag
```

枚举，应用存储空间统计信息的标志。

**起始版本：** 26.0.1

<!--Device-storageStatistics-export enum GetBundleStatsFlag--><!--Device-storageStatistics-export enum GetBundleStatsFlag-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_WITH_ALL_SIZE

```TypeScript
GET_BUNDLE_WITH_ALL_SIZE = 0x00000000
```

获取应用的全部数据大小。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetBundleStatsFlag-GET_BUNDLE_WITH_ALL_SIZE = 0x00000000--><!--Device-GetBundleStatsFlag-GET_BUNDLE_WITH_ALL_SIZE = 0x00000000-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_WITHOUT_CACHE_SIZE

```TypeScript
GET_BUNDLE_WITHOUT_CACHE_SIZE = 0x00000004
```

不包含应用缓存文件大小。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_CACHE_SIZE = 0x00000004--><!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_CACHE_SIZE = 0x00000004-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_WITHOUT_DATA_SIZE

```TypeScript
GET_BUNDLE_WITHOUT_DATA_SIZE = 0x00000002
```

不包含应用文件存储大小。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_DATA_SIZE = 0x00000002--><!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_DATA_SIZE = 0x00000002-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## GET_BUNDLE_WITHOUT_INSTALL_SIZE

```TypeScript
GET_BUNDLE_WITHOUT_INSTALL_SIZE = 0x00000001
```

不包含应用安装文件大小。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_INSTALL_SIZE = 0x00000001--><!--Device-GetBundleStatsFlag-GET_BUNDLE_WITHOUT_INSTALL_SIZE = 0x00000001-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。
