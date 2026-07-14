# LocalFilePresentStatus（系统接口）

检测结果对象，包含应用包名及其在云盘存储空间内是否存在未上云文件的状态信息。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## isLocalFilePresent

```TypeScript
isLocalFilePresent: boolean
```

该应用在云盘存储空间内是否存在尚未同步至云端的本地文件。true 表示存在， false 表示不存在。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

