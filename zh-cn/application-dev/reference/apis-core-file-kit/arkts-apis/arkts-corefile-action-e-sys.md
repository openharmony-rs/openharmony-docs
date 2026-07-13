# Action（系统接口）

清理本地云相关数据时的Action，为枚举类型。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## RETAIN_DATA

```TypeScript
RETAIN_DATA = 0
```

仅清除云端标识，保留本地缓存文件。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## CLEAR_DATA

```TypeScript
CLEAR_DATA = 1
```

清除云端标识信息，若存在本地缓存文件，一并删除。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

