# @ohos.file.storageStatistics

该模块提供空间查询相关的常用功能：包括对内外卡的空间查询、对应用分类数据统计的查询、对应用数据的查询等。

**起始版本：** 8

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentBundleInodes](arkts-corefile-getcurrentbundleinodes-f.md#getcurrentbundleinodes-1) | 获取当前应用的inode占用量，使用Promise异步回调。 |
| [getCurrentBundleStats](arkts-corefile-getcurrentbundlestats-f.md#getcurrentbundlestats-1) | 应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。 |
| [getCurrentBundleStats](arkts-corefile-getcurrentbundlestats-f.md#getcurrentbundlestats-2) | 应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeInodes](arkts-corefile-getfreeinodes-f.md#getfreeinodes-1) | 获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-getfreesize-f.md#getfreesize-2) | 获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalInodes](arkts-corefile-gettotalinodes-f.md#gettotalinodes-1) | 获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getTotalSize](arkts-corefile-gettotalsize-f.md#gettotalsize-2) | 获取内置存储的总空间大小（单位为Byte），以Promise方式返回。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllExtBundleStats](arkts-corefile-getallextbundlestats-f-sys.md#getallextbundlestats-1) | 获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。 |
| [getBundleStats](arkts-corefile-getbundlestats-f-sys.md#getbundlestats-1) | 异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。 |
| [getBundleStats](arkts-corefile-getbundlestats-f-sys.md#getbundlestats-2) | 异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getExtBundleStats](arkts-corefile-getextbundlestats-f-sys.md#getextbundlestats-1) | 获取指定用户、指定系统应用包名或系统服务名称的空间占用详情。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-getfreesize-f-sys.md#getfreesize-1) | 获取内置存储的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-getfreesizeofvolume-f-sys.md#getfreesizeofvolume-1) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-getfreesizeofvolume-f-sys.md#getfreesizeofvolume-2) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeSizeSync](arkts-corefile-getfreesizesync-f-sys.md#getfreesizesync-1) | 同步获取内置存储的可用空间大小（单位为Byte）。 |
| [getSystemDataSize](arkts-corefile-getsystemdatasize-f-sys.md#getsystemdatasize-1) | 获取系统数据的总空间大小，使用Promise异步回调。 |
| [getSystemSize](arkts-corefile-getsystemsize-f-sys.md#getsystemsize-1) | 异步获取系统数据的空间大小（单位为Byte），以callback方式返回。 |
| [getSystemSize](arkts-corefile-getsystemsize-f-sys.md#getsystemsize-2) | 异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSize](arkts-corefile-gettotalsize-f-sys.md#gettotalsize-1) | 获取内置存储的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume-1) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume-2) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSizeSync](arkts-corefile-gettotalsizesync-f-sys.md#gettotalsizesync-1) | 同步获取内置存储的总空间大小（单位为Byte）。 |
| [getUserStorageStats](arkts-corefile-getuserstoragestats-f-sys.md#getuserstoragestats-1) | 异步获取当前用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-getuserstoragestats-f-sys.md#getuserstoragestats-2) | 异步获取当前用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [getUserStorageStats](arkts-corefile-getuserstoragestats-f-sys.md#getuserstoragestats-3) | 异步获取指定用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-getuserstoragestats-f-sys.md#getuserstoragestats-4) | 异步获取指定用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [listUserdataDirInfo](arkts-corefile-listuserdatadirinfo-f-sys.md#listuserdatadirinfo-1) | 查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。 |
| [setExtBundleStats](arkts-corefile-setextbundlestats-f-sys.md#setextbundlestats-1) | 系统应用或系统服务上报自身的空间占用信息。使用Promise异步回调。&gt; **说明**：&gt;&gt; 入参stats中的flag为false时，businessName必须为某个应用的包名。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleStats](arkts-corefile-bundlestats-i.md) | 获取捆绑包统计信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExtBundleStats](arkts-corefile-extbundlestats-i-sys.md) | 系统应用或系统服务的空间占用详情。 |
| [StorageStats](arkts-corefile-storagestats-i-sys.md) |  |
| [UserdataDirInfo](arkts-corefile-userdatadirinfo-i-sys.md) | 用户设备中/data目录下的空间占用详情。 |
<!--DelEnd-->

