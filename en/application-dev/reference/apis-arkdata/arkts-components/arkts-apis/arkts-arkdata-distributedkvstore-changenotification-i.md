# ChangeNotification

```TypeScript
interface ChangeNotification
```

Defines the content of a data change notification, including inserted data, updated data, deleted data, and device ID.

**Since:** 9

<!--Device-distributedKVStore-interface ChangeNotification--><!--Device-distributedKVStore-interface ChangeNotification-End-->

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

<!--Device-ChangeNotification-deleteEntries: Entry[]--><!--Device-ChangeNotification-deleteEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId: string
```

UUID of the device.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChangeNotification-deviceId: string--><!--Device-ChangeNotification-deviceId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## insertEntries

```TypeScript
insertEntries: Entry[]
```

Data inserted.

**Type:** [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChangeNotification-insertEntries: Entry[]--><!--Device-ChangeNotification-insertEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## updateEntries

```TypeScript
updateEntries: Entry[]
```

Data updated.

**Type:** [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChangeNotification-updateEntries: Entry[]--><!--Device-ChangeNotification-updateEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
