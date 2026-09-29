# ChangeData

```TypeScript
interface ChangeData
```

Represents the data change information.

**Since:** 12

<!--Device-cloudSync-interface ChangeData--><!--Device-cloudSync-interface ChangeData-End-->

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

<!--Device-ChangeData-isDirectory: Array<boolean>--><!--Device-ChangeData-isDirectory: Array<boolean>-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## type

```TypeScript
type: NotifyType
```

Type of the data change.

**Type:** [NotifyType](arkts-corefile-cloudsync-notifytype-e.md)

**Since:** 12

<!--Device-ChangeData-type: NotifyType--><!--Device-ChangeData-type: NotifyType-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uris

```TypeScript
uris: Array<string>
```

List of URIs whose data needs to be changed.

**Type:** Array&lt;string&gt;

**Since:** 12

<!--Device-ChangeData-uris: Array<string>--><!--Device-ChangeData-uris: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
