# @ohos.file.storageStatistics

该模块提供空间查询相关的常用功能：包括对内置存储和外置存储卡的空间查询、对应用分类数据统计的查询、 对应用数据的查询、对文件系统inode资源（总量、剩余量及当前应用占用量）的查询等。适用于存储空间管理、 系统监控、应用存储优化等场景，帮助开发者实时掌握设备存储和inode资源使用情况，合理规划存储策略， 避免因存储空间或inode资源不足导致应用异常。

**起始版本：** 23

<!--Device-unnamed-declare namespace storageStatistics--><!--Device-unnamed-declare namespace storageStatistics-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentBundleInodes](arkts-corefile-storagestatistics-getcurrentbundleinodes-f.md) | 获取当前应用的inode占用量，使用Promise异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md) | 应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md) | 应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeInodes](arkts-corefile-storagestatistics-getfreeinodes-f.md) | 获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getTotalInodes](arkts-corefile-storagestatistics-gettotalinodes-f.md) | 获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllExtBundleStats](arkts-corefile-storagestatistics-getallextbundlestats-f-sys.md) | 获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md) | 异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md) | 异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getExtBundleStats](arkts-corefile-storagestatistics-getextbundlestats-f-sys.md) | 获取指定用户、指定系统应用包名或系统服务名称的空间占用详情。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f-sys.md) | 获取内置存储的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f-sys.md) | 获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeSizeSync](arkts-corefile-storagestatistics-getfreesizesync-f-sys.md) | 同步获取内置存储的可用空间大小（单位为Byte）。 |
| [getSystemDataSize](arkts-corefile-storagestatistics-getsystemdatasize-f-sys.md) | 获取系统数据的总空间大小，使用Promise异步回调。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md) | 异步获取系统数据的空间大小（单位为Byte），以callback方式返回。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md) | 异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f-sys.md) | 获取内置存储的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f-sys.md) | 获取内置存储的总空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSizeSync](arkts-corefile-storagestatistics-gettotalsizesync-f-sys.md) | 同步获取内置存储的总空间大小（单位为Byte）。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md) | 异步获取当前用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md) | 异步获取当前用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md) | 异步获取指定用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md) | 异步获取指定用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [listUserdataDirInfo](arkts-corefile-storagestatistics-listuserdatadirinfo-f-sys.md) | 查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。 |
| [setExtBundleStats](arkts-corefile-storagestatistics-setextbundlestats-f-sys.md) | 系统应用或系统服务上报自身的空间占用信息。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md) | 获取捆绑包统计信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExtBundleStats](arkts-corefile-storagestatistics-extbundlestats-i-sys.md) | 系统应用或系统服务的空间占用详情。 |
| [StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md) |  |
| [UserdataDirInfo](arkts-corefile-storagestatistics-userdatadirinfo-i-sys.md) | 用户设备中/data目录下的空间占用详情。 |
<!--DelEnd-->

