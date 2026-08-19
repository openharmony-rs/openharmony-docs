# DownloadProgress

全量下载任务的进度信息。

**起始版本：** 23

<!--Device-cloudSyncManager-class DownloadProgress--><!--Device-cloudSyncManager-class DownloadProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## downloadedSize

```TypeScript
downloadedSize: long
```

已下载数据大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** long

**起始版本：** 23

<!--Device-DownloadProgress-downloadedSize: long--><!--Device-DownloadProgress-downloadedSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## failedCount

```TypeScript
failedCount: int
```

下载失败的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** int

**起始版本：** 23

<!--Device-DownloadProgress-failedCount: int--><!--Device-DownloadProgress-failedCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## state

```TypeScript
state: DownloadState
```

下载任务的状态。

**类型：** [DownloadState](arkts-corefile-cloudsyncmanager-downloadstate-e.md)

**起始版本：** 23

<!--Device-DownloadProgress-state: DownloadState--><!--Device-DownloadProgress-state: DownloadState-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## stopReason

```TypeScript
stopReason: DownloadStopReason
```

下载停止的原因。

**类型：** [DownloadStopReason](arkts-corefile-cloudsyncmanager-downloadstopreason-e.md)

**起始版本：** 23

<!--Device-DownloadProgress-stopReason: DownloadStopReason--><!--Device-DownloadProgress-stopReason: DownloadStopReason-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## successfulCount

```TypeScript
successfulCount: int
```

已下载的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** int

**起始版本：** 23

<!--Device-DownloadProgress-successfulCount: int--><!--Device-DownloadProgress-successfulCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalCount

```TypeScript
totalCount: int
```

待下载文件总个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** int

**起始版本：** 23

<!--Device-DownloadProgress-totalCount: int--><!--Device-DownloadProgress-totalCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalSize

```TypeScript
totalSize: long
```

需要下载文件的总大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** long

**起始版本：** 23

<!--Device-DownloadProgress-totalSize: long--><!--Device-DownloadProgress-totalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

