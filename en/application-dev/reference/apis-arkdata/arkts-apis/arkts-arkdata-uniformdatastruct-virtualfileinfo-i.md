# VirtualFileInfo

```TypeScript
interface VirtualFileInfo
```

Defines a virtual root and the callbacks used by UDMF to serve it after a successful drag drop. Callback state remains in the source process and is never returned by a target-side get operation.

**Since:** 26.1.0

<!--Device-uniformDataStruct-interface VirtualFileInfo--><!--Device-uniformDataStruct-interface VirtualFileInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## onCancel

```TypeScript
onCancel?: VirtualFileOnCancel
```

Optional cancellation callback. If omitted, cancellation succeeds without notifying the provider.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileInfo-onCancel?: VirtualFileOnCancel--><!--Device-VirtualFileInfo-onCancel?: VirtualFileOnCancel-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## onRead

```TypeScript
onRead: VirtualFileOnRead
```

On-demand read callback.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileInfo-onRead: VirtualFileOnRead--><!--Device-VirtualFileInfo-onRead: VirtualFileOnRead-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## onStat

```TypeScript
onStat?: VirtualFileOnStat
```

Optional metadata callback used to obtain current file metadata.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileInfo-onStat?: VirtualFileOnStat--><!--Device-VirtualFileInfo-onStat?: VirtualFileOnStat-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## itemInfo

```TypeScript
itemInfo: VirtualItemType
```

Virtual file or directory used as the root item.

**Type:** [VirtualItemType](arkts-arkdata-uniformdatastruct-virtualitemtype-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VirtualFileInfo-itemInfo: VirtualItemType--><!--Device-VirtualFileInfo-itemInfo: VirtualItemType-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
