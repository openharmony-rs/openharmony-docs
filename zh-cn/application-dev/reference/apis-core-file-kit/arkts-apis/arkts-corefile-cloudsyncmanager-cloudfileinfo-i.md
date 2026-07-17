# CloudFileInfo

应用本地和云端文件个数以及大小信息。

**起始版本：** 20

<!--Device-cloudSyncManager-interface CloudFileInfo--><!--Device-cloudSyncManager-interface CloudFileInfo-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## bothFileCount

```TypeScript
bothFileCount: number
```

本地已上传云端的文件总个数，取值范围[0, INT32_MAX]，单位：个。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-bothFileCount: int--><!--Device-CloudFileInfo-bothFileCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## bothFileTotalSize

```TypeScript
bothFileTotalSize: number
```

本地已上传云端的文件总大小，取值范围[0, INT64_MAX]，单位：Byte。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-bothFileTotalSize: long--><!--Device-CloudFileInfo-bothFileTotalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## cloudFileCount

```TypeScript
cloudFileCount: number
```

本地未下载的云端文件总个数，取值范围[0, INT32_MAX]，单位：个。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-cloudFileCount: int--><!--Device-CloudFileInfo-cloudFileCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## cloudFileTotalSize

```TypeScript
cloudFileTotalSize: number
```

本地未下载的云端文件总大小，取值范围[0, INT64_MAX]，单位：Byte。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-cloudFileTotalSize: long--><!--Device-CloudFileInfo-cloudFileTotalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## localFileCount

```TypeScript
localFileCount: number
```

本地未上传云端的文件总个数，取值范围[0, INT32_MAX]，单位：个。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-localFileCount: int--><!--Device-CloudFileInfo-localFileCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

## localFileTotalSize

```TypeScript
localFileTotalSize: number
```

本地未上传云端的文件总大小，取值范围[0, INT64_MAX]，单位：Byte。

**类型：** number

**起始版本：** 20

<!--Device-CloudFileInfo-localFileTotalSize: long--><!--Device-CloudFileInfo-localFileTotalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

