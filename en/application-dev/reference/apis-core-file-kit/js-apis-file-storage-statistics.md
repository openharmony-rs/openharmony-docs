# @ohos.file.storageStatistics (Application Storage Statistics)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @gzhuangzhuang-->
<!--Designer: @renguang1116; @wang_zhangjun-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=a3e664c24fc6a7c3bd66829309f9260c697112dd translatedAt=2026-11-04T04:30:14.582Z pushedAt=2026-11-04T10:12:33.487Z nl=1 -->

This module provides common space query functions, including space queries for built-in storage and external storage cards, queries for application category data statistics, queries for application data, and queries for file system inode resources (total, remaining, and current application occupancy). It is applicable to scenarios such as storage space management, system monitoring, and application storage optimization, helping developers monitor device storage and inode resource usage in real time, plan storage strategies properly, and avoid application exceptions caused by insufficient storage space or inode resources.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { storageStatistics } from '@kit.CoreFileKit';
```

## storageStatistics.getCurrentBundleStats<sup>9+</sup>

getCurrentBundleStats(): Promise&lt;BundleStats&gt;

Obtains the storage space size (in bytes) of the current application. This API uses a promise to return the result.

For example, it can be used in the storage management or settings page of an application to display the storage space occupied by the current application, helping users understand the storage usage of the application.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value**

  | Type                                       | Description                      |
  | ------------------------------------------ | -------------------------- |
  | Promise&lt;[BundleStats](#bundlestats9)&gt; | Promise object, which returns the storage space size of the current application, in bytes.      |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats().then((bundleStats: storageStatistics.BundleStats) => {
  console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleStats failed. Code: ${err.code}, message: ${err.message}`);
});
```

## storageStatistics.getCurrentBundleStats<sup>9+</sup>

getCurrentBundleStats(callback: AsyncCallback&lt;BundleStats&gt;): void

Obtains the storage space size (in bytes) of the current application. This API uses an asynchronous callback to return the result.

For example, it can be used in the storage management or settings page of an application to display the storage space occupied by the current application, helping users understand the storage usage of the application.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters**

  | Name   | Type                                                      | Mandatory | Description                                |
  | -------- | --------------------------------------------------------- | ---- | ------------------------------------ |
  | callback | AsyncCallback&lt;[BundleStats](#bundlestats9)&gt;          | Yes   | Callback function invoked after obtaining the storage space size of the current application.<br>Callback parameters include:<br>err: error information, which is undefined when the call succeeds.<br>bundleStats: storage statistics of the current application. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats((error: BusinessError, bundleStats: storageStatistics.BundleStats) => {
  if (error) {
    console.error(`getCurrentBundleStats failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // Do something.
    console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
  }
});
```

## storageStatistics.getTotalSize<sup>15+</sup>

getTotalSize(): Promise&lt;number&gt;

Obtains the total size (in bytes) of the built-in storage. This API uses a promise to return the result.

Compared with getTotalSizeSync, this method does not block the current thread and is applicable to scenarios where blocking must be avoided.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value**

| Type                 | Description                                               |
| --------------------- | --------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the total built-in storage space obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message      |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize().then((totalSize: number) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError) => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

## storageStatistics.getTotalSize<sup>15+</sup>

getTotalSize(callback: AsyncCallback&lt;number&gt;): void

Obtains the total size (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result.

Compared with getTotalSizeSync, this method does not block the current thread and is applicable to scenarios where blocking must be avoided.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters**

| Name  | Type                       | Mandatory| Description                              |
| -------- | --------------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback function invoked after obtaining the total space size of built-in storage.<br>Callback parameters include:<br>err: Error information, which is undefined when the call succeeds.<br>number: Total space size of built-in storage, in bytes. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error.                                                   |
| 13900042 | Unknown error.                                               |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize((error: BusinessError, totalSize: number) => {
  if (error) {
    console.error(`getTotalSize failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // Do something.
    console.info('getTotalSize successfully:' + totalSize);
  }
});
```

## storageStatistics.getTotalSizeSync<sup>15+</sup>

getTotalSizeSync(): number

Synchronously obtains the total space size (in bytes) of the built-in storage. This method is a synchronous call and may briefly block the current thread. It is applicable to scenarios where the result is required immediately and a brief blocking is acceptable.

For example, it can be used in storage management applications to quickly display the total capacity of the device's built-in storage. To avoid blocking, use the getTotalSize asynchronous API.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value**

| Type  | Description                                  |
| ------ | -------------------------------------- |
| number | Built-in storage space obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message      |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let totalSize = storageStatistics.getTotalSizeSync();
  console.info('getTotalSizeSync successfully:' + totalSize);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`getTotalSizeSync failed. Code: ${error.code}, message: ${error.message}`);
}
```

## storageStatistics.getFreeSize<sup>15+</sup>

getFreeSize(): Promise&lt;number&gt;

Obtains the available space (in bytes) of the built-in storage. This API uses a promise to return the result.

Compared with getFreeSizeSync, this method does not block the current thread and is applicable to scenarios where blocking must be avoided.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value**

| Type                 | Description                                                 |
| --------------------- | ----------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the available space of the built-in storage obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message      |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize().then((freeSize: number) => {
  console.info('getFreeSize successfully:' + freeSize);
}).catch((err: BusinessError) => {
  console.error(`getFreeSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

## storageStatistics.getFreeSize<sup>15+</sup>

getFreeSize(callback: AsyncCallback&lt;number&gt;): void

Obtains the available space (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result.

Compared with getFreeSizeSync, this method does not block the current thread and is applicable to scenarios where blocking must be avoided.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters**

| Name  | Type                       | Mandatory| Description                                |
| -------- | --------------------------- | ---- | ------------------------------------ |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback used to obtain the available space size of built-in storage.<br>Callback parameters include:<br>err: error information, undefined when the call succeeds.<br>number: available space size of built-in storage, in Byte. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error.                                                   |
| 13900042 | Unknown error.                                               |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize((error: BusinessError, freeSize: number) => {
  if (error) {
    console.error(`getFreeSize failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // Do something.
    console.info('getFreeSize successfully:' + freeSize);
  }
});
```

## storageStatistics.getFreeSizeSync<sup>15+</sup>

getFreeSizeSync(): number

Synchronously obtains the available space (in bytes) of the built-in storage. This method is a synchronous call and may briefly block the current thread. It is applicable to scenarios where the result is required immediately and a brief block is acceptable.

For example, it can be used in storage management applications to quickly display the remaining available storage space of the device. To avoid blocking, use the asynchronous getFreeSize() API.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value**

| Type  | Description                                    |
| ------ | ---------------------------------------- |
| number | Available space of the built-in storage obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message      |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let freeSize = storageStatistics.getFreeSizeSync();
  console.info('getFreeSizeSync successfully:' + freeSize);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`getFreeSizeSync failed. Code: ${error.code}, message: ${error.message}`);
}
```

## BundleStats<sup>9+</sup>

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

| Name                   | Type                                         | Read-Only| Optional| Description                                      |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| appSize   | number  | No| No| Size of the application installation files, in bytes.   |
| cacheSize | number  | No| No | Size of the application cache files, in bytes.  |
| dataSize  | number  | No | No  | Application file storage size (excluding application installation files), in bytes. |

## storageStatistics.getTotalInodes<sup>24+</sup>

getTotalInodes(): Promise&lt;number&gt;

Obtains the total number of inodes in the file system. Only the system data partition can be queried. This API uses a promise to return the result.

An inode is a data structure used in the file system to identify and manage files. Each file or directory occupies one inode. When an application creates a large number of small files (such as log files and cache files), it may fail to create new files due to inode resource exhaustion, even if storage space remains available.

For example, it can be used in storage management or system monitoring applications to evaluate whether the file system inode resources are sufficient.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                 | Description                                                 |
| --------------------- | ----------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the total number of inodes in the file system.               |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 13600001 | IPC error.                                                   |
| 13600016 | Failed to query the inode information of the data partition. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalInodes().then((totalInodes: number) => {
  console.info('getTotalInodes successfully:' + totalInodes);
}).catch((err: BusinessError) => {
  console.error(`getTotalInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

## storageStatistics.getFreeInodes<sup>24+</sup>

getFreeInodes(): Promise&lt;number&gt;

Obtains the remaining number of inodes in the file system. Only the system data partition can be queried. This API uses a promise to return the result.

An inode is a data structure used in the file system to identify and manage files. Each file or directory occupies one inode.

For example, in applications that frequently create small files (such as logging systems and cache management), it can be used to monitor the remaining inode count and provide early warnings to avoid file creation failures caused by inode exhaustion.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                 | Description                                                 |
| --------------------- | ----------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the remaining number of inodes in the file system.              |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 13600001 | IPC error.                                                   |
| 13600016 | Failed to query the inode information of the data partition. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getFreeInodes().then((freeInodes: number) => {
  console.info('getFreeInodes successfully:' + freeInodes);
}).catch((err: BusinessError) => {
  console.error(`getFreeInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

## storageStatistics.getCurrentBundleInodes<sup>24+</sup>

getCurrentBundleInodes(): Promise&lt;number&gt;

Obtains the inode occupancy of the current application (only the system data partition can be queried). This API uses a promise to return the result.

An inode is a data structure used in the file system to identify and manage files. Each file or directory occupies one inode.

For example, on the storage management page of an application, it can be used to display the inode usage of the current application, helping developers evaluate the application's inode occupancy to optimize file management strategies.

**System capability**: SystemCapability.FileManagement.StorageService.SpatialStatistics

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                 | Description                                                 |
| --------------------- | ----------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the inode usage of the current application.              |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 13600001 | IPC error.                                                   |
| 13600002 | File system not supported.                                   |
| 13600017 | Failed to query the inode information of the application.    |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleInodes().then((bundleInodes: number) => {
  console.info('getCurrentBundleInodes successfully:' + bundleInodes);
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```
