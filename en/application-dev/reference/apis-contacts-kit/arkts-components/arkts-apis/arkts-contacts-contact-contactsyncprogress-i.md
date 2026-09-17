# ContactSyncProgress

Information about the contact synchronization progress.

Contains the sync ID, current batch, and total batch.

**Since:** 26.0.0

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## currentBatch

```TypeScript
currentBatch: number
```

Indicates the identifier of the current batch of contacts to be synchronized.

The range of values is from 1 to totalBatches.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## syncId

```TypeScript
syncId: number
```

Indicates the sync identifier used for synchronizing all contacts.

The value should start from 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## totalBatches

```TypeScript
totalBatches: number
```

Indicates the total number of batches of contacts to be synchronized.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData
