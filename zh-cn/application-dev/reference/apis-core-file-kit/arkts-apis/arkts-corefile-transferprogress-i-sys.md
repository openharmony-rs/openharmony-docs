# TransferProgress（系统接口）

搬迁任务的进度信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## failedCount

```TypeScript
failedCount: number
```

搬迁失败的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: TransferState
```

搬迁任务的状态。

**类型：** TransferState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## stopReason

```TypeScript
stopReason: TransferStopReason
```

搬迁停止的原因。

**类型：** TransferStopReason

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## successfulCount

```TypeScript
successfulCount: number
```

已搬迁的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## totalCount

```TypeScript
totalCount: number
```

待搬迁文件总个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## totalSize

```TypeScript
totalSize: number
```

需要搬迁的文件总大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## transferredSize

```TypeScript
transferredSize: number
```

已搬迁的数据大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

