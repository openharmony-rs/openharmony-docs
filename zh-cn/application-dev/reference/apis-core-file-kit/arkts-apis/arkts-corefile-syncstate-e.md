# SyncState

端云同步状态，为枚举类型。

> **说明：**
>
> 以下同步状态发生变更时，如果应用注册了同步过程事件监听，则通过回调通知应用。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOADING

```TypeScript
UPLOADING = 0
```

上行同步中。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## UPLOAD_FAILED

```TypeScript
UPLOAD_FAILED = 1
```

上行同步失败。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOADING

```TypeScript
DOWNLOADING = 2
```

下行同步中。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## DOWNLOAD_FAILED

```TypeScript
DOWNLOAD_FAILED = 3
```

下行同步失败。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## COMPLETED

```TypeScript
COMPLETED = 4
```

同步成功。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## STOPPED

```TypeScript
STOPPED = 5
```

同步已停止。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

