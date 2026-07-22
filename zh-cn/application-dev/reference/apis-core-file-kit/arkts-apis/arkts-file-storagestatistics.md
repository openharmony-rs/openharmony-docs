# @ohos.file.storageStatistics

该模块提供空间查询相关的常用功能：包括对内外卡的空间查询、对应用分类数据统计的查询、对应用数据的查询等。

**起始版本：** 8

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
| [getCurrentBundleInodes](arkts-corefile-storagestatistics-getcurrentbundleinodes-f.md#getcurrentbundleinodes) | 获取当前应用的inode占用量，使用Promise异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getcurrentbundlestats) | 应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。 |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getcurrentbundlestats-1) | 应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeInodes](arkts-corefile-storagestatistics-getfreeinodes-f.md#getfreeinodes) | 获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f.md#getfreesize-1) | 获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalInodes](arkts-corefile-storagestatistics-gettotalinodes-f.md#gettotalinodes) | 获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f.md#gettotalsize-1) | 获取内置存储的总空间大小（单位为Byte），以Promise方式返回。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllExtBundleStats](arkts-corefile-storagestatistics-getallextbundlestats-f-sys.md#getallextbundlestats) | 获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getbundlestats) | 异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。 |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getbundlestats-1) | 异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getExtBundleStats](arkts-corefile-storagestatistics-getextbundlestats-f-sys.md#getextbundlestats) | 获取指定用户、指定系统应用包名或系统服务名称的空间占用详情。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f-sys.md#getfreesize) | 获取内置存储的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getfreesizeofvolume) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。 |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getfreesizeofvolume-1) | 异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。 |
| [getFreeSizeSync](arkts-corefile-storagestatistics-getfreesizesync-f-sys.md#getfreesizesync) | 同步获取内置存储的可用空间大小（单位为Byte）。 |
| [getSystemDataSize](arkts-corefile-storagestatistics-getsystemdatasize-f-sys.md#getsystemdatasize) | 获取系统数据的总空间大小，使用Promise异步回调。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getsystemsize) | 异步获取系统数据的空间大小（单位为Byte），以callback方式返回。 |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getsystemsize-1) | 异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f-sys.md#gettotalsize) | 获取内置存储的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以callback方式返回。 |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume-1) | 异步获取外置存储设备中指定卷设备的总空间大小（单位为Byte），以Promise方式返回。 |
| [getTotalSizeSync](arkts-corefile-storagestatistics-gettotalsizesync-f-sys.md#gettotalsizesync) | 同步获取内置存储的总空间大小（单位为Byte）。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats) | 异步获取当前用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-1) | 异步获取当前用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-2) | 异步获取指定用户各类别存储空间大小（单位为Byte），以Promise方式返回。 |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-3) | 异步获取指定用户各类别存储空间大小（单位为Byte），以callback方式返回。 |
| [listUserdataDirInfo](arkts-corefile-storagestatistics-listuserdatadirinfo-f-sys.md#listuserdatadirinfo) | 查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。 |
| [setExtBundleStats](arkts-corefile-storagestatistics-setextbundlestats-f-sys.md#setextbundlestats) | 系统应用或系统服务上报自身的空间占用信息。使用Promise异步回调。 > **说明**：  >  > 入参stats中的flag为false时，businessName必须为某个应用的包名。 |
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

