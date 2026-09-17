# DownloadProgress

Represents information about the download progress of a cloud file.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: DownloadErrorType
```

Download error type.

**Type:** [DownloadErrorType](arkts-corefile-cloudsync-downloaderrortype-e.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## processed

```TypeScript
processed: number
```

Size of the downloaded data, in bytes. The value range is [0, 9223372036854775807].

**Type:** number

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## size

```TypeScript
size: number
```

Size of the cloud file, in bytes. The value range is [0, 9223372036854775807].

**Type:** number

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: State
```

File download state.

**Type:** [State](arkts-corefile-cloudsync-state-e.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uri

```TypeScript
uri: string
```

URI of the cloud file.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
