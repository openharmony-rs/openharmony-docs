# UploadProgress（系统接口）

文件上传进度信息。

**起始版本：** 26.0.0

<!--Device-cloudSync-interface UploadProgress--><!--Device-cloudSync-interface UploadProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: ErrorType
```

上传的错误类型。

**类型：** ErrorType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UploadProgress-error: ErrorType--><!--Device-UploadProgress-error: ErrorType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## processed

```TypeScript
processed: long
```

已上传数据大小，取值范围[0, 9223372036854775807]，单位：Byte。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UploadProgress-processed: long--><!--Device-UploadProgress-processed: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: long
```

当前文件总大小，取值范围[0, 9223372036854775807]，单位：Byte。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UploadProgress-size: long--><!--Device-UploadProgress-size: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: UploadState
```

文件上传状态。

**类型：** [UploadState](arkts-corefile-cloudsync-uploadstate-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UploadProgress-state: UploadState--><!--Device-UploadProgress-state: UploadState-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

当前文件的URI。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UploadProgress-uri: string--><!--Device-UploadProgress-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

