# SyncMode

```TypeScript
enum SyncMode
```

Enumerates the sync modes.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [SyncMode](arkts-arkdata-distributedkvstore-syncmode-e.md)

<!--Device-distributedData-enum SyncMode--><!--Device-distributedData-enum SyncMode-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PULL_ONLY

```TypeScript
PULL_ONLY = 0
```

Pull data from the peer end to the local end only.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [PULL_ONLY](arkts-arkdata-distributedkvstore-syncmode-e.md#pull_only)

<!--Device-SyncMode-PULL_ONLY = 0--><!--Device-SyncMode-PULL_ONLY = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_ONLY

```TypeScript
PUSH_ONLY = 1
```

Push data from the local end to the peer end only.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [PUSH_ONLY](arkts-arkdata-distributedkvstore-syncmode-e.md#push_only)

<!--Device-SyncMode-PUSH_ONLY = 1--><!--Device-SyncMode-PUSH_ONLY = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_PULL

```TypeScript
PUSH_PULL = 2
```

Push data from the local end to the peer end and then pull data from the peer end to the local end.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [PUSH_PULL](arkts-arkdata-distributedkvstore-syncmode-e.md#push_pull)

<!--Device-SyncMode-PUSH_PULL = 2--><!--Device-SyncMode-PUSH_PULL = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
