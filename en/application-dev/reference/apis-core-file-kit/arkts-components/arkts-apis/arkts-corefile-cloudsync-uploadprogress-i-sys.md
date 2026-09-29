# UploadProgress (System API)

```TypeScript
interface UploadProgress
```

The UploadProgress data structure.

**Since:** 26.0.0

<!--Device-cloudSync-interface UploadProgress--><!--Device-cloudSync-interface UploadProgress-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: ErrorType
```

The error type of upload.

**Type:** [ErrorType](arkts-corefile-cloudsync-errortype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UploadProgress-error: ErrorType--><!--Device-UploadProgress-error: ErrorType-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## processed

```TypeScript
processed: number
```

The processed data size for current file. <br>Unit:Byte.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UploadProgress-processed: long--><!--Device-UploadProgress-processed: long-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## size

```TypeScript
size: number
```

The size of current file. <br>Unit:Byte.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UploadProgress-size: long--><!--Device-UploadProgress-size: long-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## state

```TypeScript
state: UploadState
```

The current upload state.

**Type:** [UploadState](arkts-corefile-cloudsync-uploadstate-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UploadProgress-state: UploadState--><!--Device-UploadProgress-state: UploadState-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

The uri of current file.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UploadProgress-uri: string--><!--Device-UploadProgress-uri: string-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.
