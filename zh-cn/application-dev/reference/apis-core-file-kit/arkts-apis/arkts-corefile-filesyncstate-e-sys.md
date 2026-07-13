# FileSyncState（系统接口）

端云文件同步状态，为枚举类型。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## UPLOADING

```TypeScript
UPLOADING = 0
```

上行同步中。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## DOWNLOADING

```TypeScript
DOWNLOADING = 1
```

下行同步中。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## COMPLETED

```TypeScript
COMPLETED = 2
```

同步成功。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## STOPPED

```TypeScript
STOPPED = 3
```

同步已停止。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## TO_BE_UPLOADED

```TypeScript
TO_BE_UPLOADED = 4
```

正在等待上行。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## UPLOAD_SUCCESS

```TypeScript
UPLOAD_SUCCESS = 5
```

文件已成功上行。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## UPLOAD_FAILURE

```TypeScript
UPLOAD_FAILURE = 6
```

文件上行失败。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

