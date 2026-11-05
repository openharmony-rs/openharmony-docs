# VirtualDirItem

```TypeScript
interface VirtualDirItem extends VirtualBaseItem
```

Describes a virtual directory and its optional child items.

**Inheritance/Implementation:** VirtualDirItem extends [VirtualBaseItem](arkts-arkdata-uniformdatastruct-virtualbaseitem-i.md)

**Since:** 26.1.0

<!--Device-uniformDataStruct-interface VirtualDirItem extends VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualDirItem extends VirtualBaseItem-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## subItems

```TypeScript
subItems?: Array<VirtualItemType>
```

Child items exposed when the target application enumerates this directory.

**Type:** Array&lt;[VirtualItemType](arkts-arkdata-uniformdatastruct-virtualitemtype-t.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualDirItem-subItems?: Array<VirtualItemType>--><!--Device-VirtualDirItem-subItems?: Array<VirtualItemType>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'dir'
```

Directory item discriminator.

**Type:** 'dir'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualDirItem-readonly type: 'dir'--><!--Device-VirtualDirItem-readonly type: 'dir'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
