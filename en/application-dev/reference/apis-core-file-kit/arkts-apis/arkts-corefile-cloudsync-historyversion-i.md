# HistoryVersion

Represents the historical version information of the device-cloud file when the [gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#gethistoryversionlist) method of the [FileVersion](arkts-corefile-cloudsync-fileversion-c.md) class is called.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## autoResolved

```TypeScript
autoResolved: boolean
```

Whether the current version is the one where conflicts were automatically resolved.

When the application is set to manually resolve conflicts, **false** is returned by default, which is meaningless.

When the application is set to automatically resolve conflicts, the device side automatically resolves conflicts. The value **true** means conflicts exist in the current version and have been automatically resolved by the device-cloud service; the value **false** means no conflict exists and conflicts are not automatically resolved.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## editedTime

```TypeScript
editedTime: number
```

File content modification timestamp, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## fileSize

```TypeScript
fileSize: number
```

File size in bytes.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## originalFileName

```TypeScript
originalFileName: string
```

File name of the current version.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## sha256

```TypeScript
sha256: string
```

Hash value of the file content of the current version.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## versionId

```TypeScript
versionId: string
```

File version.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
