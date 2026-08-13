# @ohos.file.storageStatistics

该模块提供空间查询相关的常用功能：包括对内外卡的空间查询、对应用分类数据统计的查询、对应用数据的查询等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace storageStatistics--><!--Device-unnamed-declare namespace storageStatistics-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentBundleInodes](arkts-corefile-storagestatistics-getcurrentbundleinodes-f.md#getCurrentBundleInodes) | 获取当前应用的inode占用量，使用Promise异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getCurrentBundleStats) | 应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getCurrentBundleStats) | 应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeInodes](arkts-corefile-storagestatistics-getfreeinodes-f.md#getFreeInodes) | 获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f.md#getFreeSize) | 获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalInodes](arkts-corefile-storagestatistics-gettotalinodes-f.md#getTotalInodes) | 获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f.md#getTotalSize) | 获取内置存储的总空间大小（单位为Byte），以Promise方式返回。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllExtBundleStats](arkts-corefile-storagestatistics-getallextbundlestats-f-sys.md#getAllExtBundleStats) | 获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getBundleStats) | 异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getBundleStats（系统接口）) | 异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getExtBundleStats](arkts-corefile-storagestatistics-getextbundlestats-f-sys.md#getExtBundleStats) | 获取指定用户、指定系统应用包名或系统服务名称的空间占用详情。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f-sys.md#getFreeSize) | 获取内置存储的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getFreeSizeOfVolume) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getFreeSizeOfVolume（系统接口）) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeSizeSync](arkts-corefile-storagestatistics-getfreesizesync-f-sys.md#getFreeSizeSync) | 同步获取内置存储的可用空间大小（单位为Byte）。 |
| [getSystemDataSize](arkts-corefile-storagestatistics-getsystemdatasize-f-sys.md#getSystemDataSize) | 获取系统数据的总空间大小，使用Promise异步回调。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getSystemSize) | 异步获取系统数据的空间大小（单位为Byte），以callback方式返回。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getSystemSize（系统接口）) | 异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f-sys.md#getTotalSize) | 获取内置存储的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#getTotalSizeOfVolume) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#getTotalSizeOfVolume（系统接口）) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSizeSync](arkts-corefile-storagestatistics-gettotalsizesync-f-sys.md#getTotalSizeSync) | 同步获取内置存储的总空间大小（单位为Byte）。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats) | 异步获取当前用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats（系统接口）) | 异步获取当前用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats（系统接口）) | 异步获取指定用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats（系统接口）) | 异步获取指定用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [listUserdataDirInfo](arkts-corefile-storagestatistics-listuserdatadirinfo-f-sys.md#listUserdataDirInfo) | 查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。 |
| [setExtBundleStats](arkts-corefile-storagestatistics-setextbundlestats-f-sys.md#setExtBundleStats) | 系统应用或系统服务上报自身的空间占用信息。使用Promise异步回调。 |
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

