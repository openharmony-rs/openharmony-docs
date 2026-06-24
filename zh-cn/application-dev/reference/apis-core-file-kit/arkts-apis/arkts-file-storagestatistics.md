# @ohos.file.storageStatistics

该模块提供空间查询相关的常用功能：包括对内外卡的空间查询、对应用分类数据统计的查询、对应用数据的查询等。

**起始版本：** 8

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getAllExtBundleStats](arkts-corefile-storagestatistics-getallextbundlestats-f-sys.md#getAllExtBundleStats-1) | 获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。<br/> |
| <!--DelRow-->[getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getBundleStats-1) | 异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getBundleStats-2) | 异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。<br/> |
| [getCurrentBundleInodes](arkts-corefile-storagestatistics-getcurrentbundleinodes-f.md#getCurrentBundleInodes-1) | 获取当前应用的inode占用量，使用Promise异步回调。<br/> |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getCurrentBundleStats-1) | 应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。<br/> |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getCurrentBundleStats-2) | 应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getExtBundleStats](arkts-corefile-storagestatistics-getextbundlestats-f-sys.md#getExtBundleStats-1) | 获取指定用户、指定系统应用包名或系统服务名称的空间占用详情。使用Promise异步回调。<br/> |
| [getFreeInodes](arkts-corefile-storagestatistics-getfreeinodes-f.md#getFreeInodes-1) | 获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。<br/> |
| <!--DelRow-->[getFreeSize](arkts-corefile-storagestatistics-getfreesize-f-sys.md#getFreeSize-1) | 获取内置存储的可用空间大小（单位为Byte），以callback方式返回。<br/> |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f.md#getFreeSize-2) | 获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getFreeSizeOfVolume-1) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getFreeSizeOfVolume-2) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getFreeSizeSync](arkts-corefile-storagestatistics-getfreesizesync-f-sys.md#getFreeSizeSync-1) | 同步获取内置存储的可用空间大小（单位为Byte）。<br/> |
| <!--DelRow-->[getSystemDataSize](arkts-corefile-storagestatistics-getsystemdatasize-f-sys.md#getSystemDataSize-1) | 获取系统数据的总空间大小，使用Promise异步回调。<br/> |
| <!--DelRow-->[getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getSystemSize-1) | 异步获取系统数据的空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getSystemSize-2) | 异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。<br/> |
| [getTotalInodes](arkts-corefile-storagestatistics-gettotalinodes-f.md#getTotalInodes-1) | 获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。<br/> |
| <!--DelRow-->[getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f-sys.md#getTotalSize-1) | 获取内置存储的总空间大小（单位为Byte），以callback方式返回。<br/> |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f.md#getTotalSize-2) | 获取内置存储的总空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#getTotalSizeOfVolume-1) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#getTotalSizeOfVolume-2) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getTotalSizeSync](arkts-corefile-storagestatistics-gettotalsizesync-f-sys.md#getTotalSizeSync-1) | 同步获取内置存储的总空间大小（单位为Byte）。<br/> |
| <!--DelRow-->[getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats-1) | 异步获取当前用户各类别存储空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats-2) | 异步获取当前用户各类别存储空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats-3) | 异步获取指定用户各类别存储空间大小（单位为Byte），以Promise方式返回。<br/> |
| <!--DelRow-->[getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getUserStorageStats-4) | 异步获取指定用户各类别存储空间大小（单位为Byte），以callback方式返回。<br/> |
| <!--DelRow-->[listUserdataDirInfo](arkts-corefile-storagestatistics-listuserdatadirinfo-f-sys.md#listUserdataDirInfo-1) | 查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。<br/> |
| <!--DelRow-->[setExtBundleStats](arkts-corefile-storagestatistics-setextbundlestats-f-sys.md#setExtBundleStats-1) | 系统应用或系统服务上报自身的空间占用信息。使用Promise异步回调。<br/><br/>&gt; **说明**：<br/>&gt;<br/>&gt; 入参stats中的flag为false时，businessName必须为某个应用的包名。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md) | 获取捆绑包统计信息。<br/> |
| <!--DelRow-->[ExtBundleStats](arkts-corefile-storagestatistics-extbundlestats-i-sys.md) | 系统应用或系统服务的空间占用详情。<br/> |
| <!--DelRow-->[StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md) |  |
| <!--DelRow-->[UserdataDirInfo](arkts-corefile-storagestatistics-userdatadirinfo-i-sys.md) | 用户设备中/data目录下的空间占用详情。<br/> |

