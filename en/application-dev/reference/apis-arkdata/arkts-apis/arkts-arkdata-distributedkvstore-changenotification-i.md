# ChangeNotification

Defines the content of a data change notification, including inserted data, updated data, deleted data, and device ID.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## deleteEntries

```TypeScript
deleteEntries: Entry[]
```

Data deleted.

**Type:** [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId: string
```

UUID of the device.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## insertEntries

```TypeScript
insertEntries: Entry[]
```

Data inserted.

**Type:** [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## updateEntries

```TypeScript
updateEntries: Entry[]
```

Data updated.

**Type:** [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
