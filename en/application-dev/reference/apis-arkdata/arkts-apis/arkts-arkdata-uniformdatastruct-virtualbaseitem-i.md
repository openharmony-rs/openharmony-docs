# VirtualBaseItem

```TypeScript
interface VirtualBaseItem
```

Describes the common metadata of a virtual file system item used for on-demand drag data.

**Since:** 26.1.0

<!--Device-uniformDataStruct-interface VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualBaseItem-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## modifyTime

```TypeScript
modifyTime: number
```

Last modification time, in milliseconds since the Unix epoch.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualBaseItem-modifyTime: long--><!--Device-VirtualBaseItem-modifyTime: long-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## name

```TypeScript
name: string
```

Item name. The value cannot contain a slash, backslash, **.**, or **..**, and is at most 255 bytes.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualBaseItem-name: string--><!--Device-VirtualBaseItem-name: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'file' | 'dir'
```

Item type.

**Type:** 'file' &#124; 'dir'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualBaseItem-readonly type: 'file' | 'dir'--><!--Device-VirtualBaseItem-readonly type: 'file' | 'dir'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
