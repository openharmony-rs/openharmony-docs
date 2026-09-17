# ProgressInfo

Represents the progress information.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## progress

```TypeScript
progress: number
```

Progress of the drag task, in percentage.

The value is an integer ranging from -1 to 100. The value **-1** indicates a failure to obtain data, and the value **100** indicates data is obtained.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## status

```TypeScript
status: ListenerStatus
```

Status code of the drag task reported by the system.

**Type:** [ListenerStatus](arkts-arkdata-unifieddatachannel-listenerstatus-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
