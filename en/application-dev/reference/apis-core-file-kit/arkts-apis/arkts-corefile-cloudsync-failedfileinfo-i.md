# FailedFileInfo

```TypeScript
interface FailedFileInfo
```

Represents a list of files that fail to be downloaded from the Drive Kit and failure causes.

**Since:** 20

<!--Device-cloudSync-interface FailedFileInfo--><!--Device-cloudSync-interface FailedFileInfo-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## error

```TypeScript
error: DownloadErrorType
```

Error type of the file download failure.

**Type:** [DownloadErrorType](arkts-corefile-cloudsync-downloaderrortype-e.md)

**Since:** 20

<!--Device-FailedFileInfo-error: DownloadErrorType--><!--Device-FailedFileInfo-error: DownloadErrorType-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uri

```TypeScript
uri: string
```

URI of the file that fails to be downloaded.

**Type:** string

**Since:** 20

<!--Device-FailedFileInfo-uri: string--><!--Device-FailedFileInfo-uri: string-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
