# ContactSyncInfo

Information about contact synchronization for the calling application.

**Since:** 26.0.0

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## completedBatches

```TypeScript
completedBatches: Array<number>
```

Indicates the array of batch identifiers for contacts that have been synchronized successfully.

The range of values is from 1 to totalBatches.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## lastSyncTime

```TypeScript
lastSyncTime: number
```

Indicates the latest timestamp the contacts were synchronized in milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## mode

```TypeScript
mode: ContactSyncMode
```

The contact synchronization mode.

**Type:** [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## syncId

```TypeScript
syncId: number
```

Indicates the sync identifier used for synchronizing all contacts.

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
