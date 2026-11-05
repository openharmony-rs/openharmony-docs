# VirtualFileItem

```TypeScript
interface VirtualFileItem extends VirtualBaseItem
```

Describes a virtual file whose bytes are provided on demand.

**Inheritance/Implementation:** VirtualFileItem extends [VirtualBaseItem](arkts-arkdata-uniformdatastruct-virtualbaseitem-i.md)

**Since:** 26.1.0

<!--Device-uniformDataStruct-interface VirtualFileItem extends VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualFileItem extends VirtualBaseItem-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## id

```TypeScript
id: string
```

Identifier passed to virtual file callbacks. The value is at most 1024 bytes.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileItem-id: string--><!--Device-VirtualFileItem-id: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## size

```TypeScript
size: number
```

Required file size in bytes. It must be a non-negative integer; zero represents an empty file.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileItem-size: long--><!--Device-VirtualFileItem-size: long-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'file'
```

File item discriminator.

**Type:** 'file'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileItem-readonly type: 'file'--><!--Device-VirtualFileItem-readonly type: 'file'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
