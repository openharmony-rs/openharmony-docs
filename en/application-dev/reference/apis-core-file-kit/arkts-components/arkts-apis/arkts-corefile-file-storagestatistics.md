# @ohos.file.storageStatistics(Application Storage Statistics)

The **storageStatistics** module provides APIs for obtaining storage space information, including the space of built-in and plug-in memory cards, space occupied by different types of data, and space of application data.

**Since:** 8

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getCurrentBundleInodes](arkts-corefile-storagestatistics-getcurrentbundleinodes-f.md) | Get the current bundle inodes. |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getcurrentbundlestats) | Obtains the storage space (in bytes) of this application. This API uses an asynchronous callback to return the result. |
| [getCurrentBundleStats](arkts-corefile-storagestatistics-getcurrentbundlestats-f.md#getcurrentbundlestats-1) | Obtains the storage space (in bytes) of this application. This API uses a promise to return the result. |
| [getFreeInodes](arkts-corefile-storagestatistics-getfreeinodes-f.md) | Get the free inodes. |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f.md#getfreesize) | Obtains the available space (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result. |
| [getFreeSize](arkts-corefile-storagestatistics-getfreesize-f.md#getfreesize-1) | Obtains the available space (in bytes) of the built-in storage. This API uses a promise to return the result. |
| [getFreeSizeSync](arkts-corefile-storagestatistics-getfreesizesync-f.md) | Obtains the available space of the built-in storage, in bytes. This API returns the result synchronously. |
| [getTotalInodes](arkts-corefile-storagestatistics-gettotalinodes-f.md) | Get the total inodes. |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f.md#gettotalsize) | Obtains the total size (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result. |
| [getTotalSize](arkts-corefile-storagestatistics-gettotalsize-f.md#gettotalsize-1) | Obtains the total size (in bytes) of the built-in storage. This API uses a promise to return the result. |
| [getTotalSizeSync](arkts-corefile-storagestatistics-gettotalsizesync-f.md) | Obtains the total space of the built-in storage, in bytes. This API returns the result synchronously. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllExtBundleStats](arkts-corefile-storagestatistics-getallextbundlestats-f-sys.md) | Obtains the space usage of all system applications or system services of a specified user. This API uses a promise to return the result. |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getbundlestats) | Obtains the storage space of an application, in bytes. This API uses an asynchronous callback to return the result. |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getbundlestats-1) | Obtains the storage space of an application, in bytes. This API uses a promise to return the result. |
| [getBundleStats](arkts-corefile-storagestatistics-getbundlestats-f-sys.md#getbundlestats-2) | Obtains the storage space of an application, in bytes. This API uses a promise to return the result. |
| [getExtBundleStats](arkts-corefile-storagestatistics-getextbundlestats-f-sys.md) | Obtains the space usage of a specified user, system application bundle name, or system service name. This API uses a promise to return the result. |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getfreesizeofvolume) | Get the free size of volume. |
| [getFreeSizeOfVolume](arkts-corefile-storagestatistics-getfreesizeofvolume-f-sys.md#getfreesizeofvolume-1) | Get the free size of volume. |
| [getSystemDataSize](arkts-corefile-storagestatistics-getsystemdatasize-f-sys.md) | Get the system data size. |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getsystemsize) | Get the system size. |
| [getSystemSize](arkts-corefile-storagestatistics-getsystemsize-f-sys.md#getsystemsize-1) | Get the system size. |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume) | Get the total size of volume. |
| [getTotalSizeOfVolume](arkts-corefile-storagestatistics-gettotalsizeofvolume-f-sys.md#gettotalsizeofvolume-1) | Get the total size of volume. |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats) | Obtains the storage statistics of this user, in bytes. This API uses a promise to return the result. |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-1) | Obtains the storage statistics of this user, in bytes. This API uses an asynchronous callback to return the result. |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-2) | Obtains the storage statistics of the specified user, in bytes. This API uses a promise to return the result. |
| [getUserStorageStats](arkts-corefile-storagestatistics-getuserstoragestats-f-sys.md#getuserstoragestats-3) | Obtains the storage statistics of the specified user, in bytes. This API uses an asynchronous callback to return the result. |
| [listUserdataDirInfo](arkts-corefile-storagestatistics-listuserdatadirinfo-f-sys.md) | Queries the space usage of the **\/data** directory on the user device. This API uses a promise to return the result. |
| [setExtBundleStats](arkts-corefile-storagestatistics-setextbundlestats-f-sys.md) | Reports the space usage of system applications or system services. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md) | Get the bundle statistics. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleStatsOptions](arkts-corefile-storagestatistics-bundlestatsoptions-i-sys.md) | Options for obtaining the bundle statistics. |
| [ExtBundleStats](arkts-corefile-storagestatistics-extbundlestats-i-sys.md) | Details the space usage of system applications or system services. |
| [StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md) | Get the user storage statistics. |
| [UserdataDirInfo](arkts-corefile-storagestatistics-userdatadirinfo-i-sys.md) | Details the space usage of the **\/data** directory on the user device. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [GetBundleStatsFlag](arkts-corefile-storagestatistics-getbundlestatsflag-e-sys.md) | Enumerates the flags for obtaining the bundle statistics. |
<!--DelEnd-->
