# ChangeData

Represents the data change information.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## isDirectory

```TypeScript
isDirectory: Array<boolean>
```

Whether the URIs with data changed are of directories. The value **true** means the URIs are of directories; the value **false** means the opposite.

**Type:** Array&lt;boolean&gt;

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## type

```TypeScript
type: NotifyType
```

Type of the data change.

**Type:** [NotifyType](arkts-corefile-cloudsync-notifytype-e.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uris

```TypeScript
uris: Array<string>
```

List of URIs whose data needs to be changed.

**Type:** Array&lt;string&gt;

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
