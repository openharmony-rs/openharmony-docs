# ProgressDetails

Describes detail of the cloud sync `Progress`.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## code

```TypeScript
code: ProgressCode
```

Describes the code of data sync progress.

**Type:** [ProgressCode](arkts-arkdata-relationalstore-progresscode-e.md)

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## details

```TypeScript
details: Record<string, TableDetails>
```

Statistics of each table.

The key indicates the table name, and the value indicates the device-cloud sync statistics of the table.

**Type:** Record&lt;string, [TableDetails](arkts-arkdata-relationalstore-tabledetails-i.md)&gt;

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
message?: string
```

Indicates the code message.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## schedule

```TypeScript
schedule: Progress
```

Describes the status of data sync progress.

**Type:** [Progress](arkts-arkdata-relationalstore-progress-e.md)

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
