# ProgressInfo

```TypeScript
interface ProgressInfo
```

Defines the data for progress reporting.

**Since:** 15

<!--Device-unifiedDataChannel-interface ProgressInfo--><!--Device-unifiedDataChannel-interface ProgressInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## progress

```TypeScript
progress: number
```

Progress percentage of the drag-and-drop task reported by the system.

The value is an integer in the range [-1, 100], where -1 indicates that data acquisition failed this time, and 100 indicates that data acquisition is complete.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ProgressInfo-progress: int--><!--Device-ProgressInfo-progress: int-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## status

```TypeScript
status: ListenerStatus
```

Status code of the drag-and-drop task reported by the system.

**Type:** [ListenerStatus](arkts-arkdata-unifieddatachannel-listenerstatus-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ProgressInfo-status: ListenerStatus--><!--Device-ProgressInfo-status: ListenerStatus-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
