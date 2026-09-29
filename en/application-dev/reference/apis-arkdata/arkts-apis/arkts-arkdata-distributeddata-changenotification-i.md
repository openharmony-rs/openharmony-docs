# ChangeNotification

```TypeScript
interface ChangeNotification
```

Defines the content of data change notifications, including inserted data, updated data, deleted data, and device ID.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** ChangeNotification

<!--Device-distributedData-interface ChangeNotification--><!--Device-distributedData-interface ChangeNotification-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
```

## deleteEntries

```TypeScript
deleteEntries: Entry[]
```

Data deleted.

**Type:** [Entry](arkts-arkdata-distributeddata-entry-i.md)[]

**Since:** 7

**Deprecated since:** 9

**Substitutes:** deleteEntries

<!--Device-ChangeNotification-deleteEntries: Entry[]--><!--Device-ChangeNotification-deleteEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId: string
```

UUID of the device.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** deviceId

<!--Device-ChangeNotification-deviceId: string--><!--Device-ChangeNotification-deviceId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## insertEntries

```TypeScript
insertEntries: Entry[]
```

Data inserted.

**Type:** [Entry](arkts-arkdata-distributeddata-entry-i.md)[]

**Since:** 7

**Deprecated since:** 9

**Substitutes:** insertEntries

<!--Device-ChangeNotification-insertEntries: Entry[]--><!--Device-ChangeNotification-insertEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## updateEntries

```TypeScript
updateEntries: Entry[]
```

Data updated.

**Type:** [Entry](arkts-arkdata-distributeddata-entry-i.md)[]

**Since:** 7

**Deprecated since:** 9

**Substitutes:** updateEntries

<!--Device-ChangeNotification-updateEntries: Entry[]--><!--Device-ChangeNotification-updateEntries: Entry[]-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
