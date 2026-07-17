# DownloadProgress

云文件下载过程。

**起始版本：** 11

<!--Device-cloudSync-interface DownloadProgress--><!--Device-cloudSync-interface DownloadProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: DownloadErrorType
```

下载的错误类型。

**类型：** DownloadErrorType

**起始版本：** 11

<!--Device-DownloadProgress-error: DownloadErrorType--><!--Device-DownloadProgress-error: DownloadErrorType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## processed

```TypeScript
processed: number
```

已下载数据大小，取值范围[0，9223372036854775807]（单位：Byte）。

**类型：** number

**起始版本：** 11

<!--Device-DownloadProgress-processed: long--><!--Device-DownloadProgress-processed: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## size

```TypeScript
size: number
```

当前云文件大小，取值范围[0，9223372036854775807]（单位：Byte）。

**类型：** number

**起始版本：** 11

<!--Device-DownloadProgress-size: long--><!--Device-DownloadProgress-size: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: State
```

枚举值，云文件下载状态。

**类型：** State

**起始版本：** 11

<!--Device-DownloadProgress-state: State--><!--Device-DownloadProgress-state: State-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uri

```TypeScript
uri: string
```

当前云文件URI。

**类型：** string

**起始版本：** 11

<!--Device-DownloadProgress-uri: string--><!--Device-DownloadProgress-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

