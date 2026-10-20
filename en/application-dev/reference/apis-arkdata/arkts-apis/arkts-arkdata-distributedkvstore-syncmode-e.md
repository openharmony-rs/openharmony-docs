# SyncMode

```TypeScript
enum SyncMode
```

Enumerates the sync modes.

**Since:** 9

<!--Device-distributedKVStore-enum SyncMode--><!--Device-distributedKVStore-enum SyncMode-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PULL_ONLY

```TypeScript
PULL_ONLY
```

Pull data from the peer end to the local end only.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncMode-PULL_ONLY--><!--Device-SyncMode-PULL_ONLY-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_ONLY

```TypeScript
PUSH_ONLY
```

Push data from the local end to the peer end only.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncMode-PUSH_ONLY--><!--Device-SyncMode-PUSH_ONLY-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_PULL

```TypeScript
PUSH_PULL
```

Push data from the local end to the peer end and then pull data from the peer end to the local end.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncMode-PUSH_PULL--><!--Device-SyncMode-PUSH_PULL-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
