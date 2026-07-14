# DownloadProgress

全量下载任务的进度信息。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## downloadedSize

```TypeScript
downloadedSize: number
```

已下载数据大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## failedCount

```TypeScript
failedCount: number
```

下载失败的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## state

```TypeScript
state: DownloadState
```

下载任务的状态。

**类型：** DownloadState

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## stopReason

```TypeScript
stopReason: DownloadStopReason
```

下载停止的原因。

**类型：** DownloadStopReason

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## successfulCount

```TypeScript
successfulCount: number
```

已下载的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalCount

```TypeScript
totalCount: number
```

待下载文件总个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## totalSize

```TypeScript
totalSize: number
```

需要下载文件的总大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

