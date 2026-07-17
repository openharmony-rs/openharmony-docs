# VersionDownloadProgress

历史版本文件下载状态和进度信息，调用端云文件版本管理类[FileVersion](arkts-corefile-cloudsync-fileversion-c.md)的[downloadHistoryVersion](arkts-corefile-cloudsync-fileversion-c.md#downloadhistoryversion-1)方法时，回调函数的入参类型。

**起始版本：** 20

<!--Device-cloudSync-interface VersionDownloadProgress--><!--Device-cloudSync-interface VersionDownloadProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## errType

```TypeScript
errType: DownloadErrorType
```

返回批量缓存任务执行失败时的错误类型。

**类型：** DownloadErrorType

**起始版本：** 20

<!--Device-VersionDownloadProgress-errType: DownloadErrorType--><!--Device-VersionDownloadProgress-errType: DownloadErrorType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## progress

```TypeScript
progress: number
```

下载进度，单位：百分比。

**类型：** number

**起始版本：** 20

<!--Device-VersionDownloadProgress-progress: int--><!--Device-VersionDownloadProgress-progress: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: State
```

所选版本云文件的下载状态。

**类型：** State

**起始版本：** 20

<!--Device-VersionDownloadProgress-state: State--><!--Device-VersionDownloadProgress-state: State-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

