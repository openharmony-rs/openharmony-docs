# KVStoreType

```TypeScript
enum KVStoreType
```

Enumerates the KV store types.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [KVStoreType](arkts-arkdata-distributedkvstore-kvstoretype-e.md)

<!--Device-distributedData-enum KVStoreType--><!--Device-distributedData-enum KVStoreType-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## DEVICE_COLLABORATION

```TypeScript
DEVICE_COLLABORATION = 0
```

Device KV store.

The device KV store manages data by device, which eliminates conflicts. Data can be queried by device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [DEVICE_COLLABORATION](arkts-arkdata-distributedkvstore-kvstoretype-e.md#device_collaboration)

<!--Device-KVStoreType-DEVICE_COLLABORATION = 0--><!--Device-KVStoreType-DEVICE_COLLABORATION = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## MULTI_VERSION

```TypeScript
MULTI_VERSION = 2
```

Multi-version KV store. This type is not supported currently.

**Since:** 7

**Deprecated since:** 9

<!--Device-KVStoreType-MULTI_VERSION = 2--><!--Device-KVStoreType-MULTI_VERSION = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## SINGLE_VERSION

```TypeScript
SINGLE_VERSION = 1
```

Single KV store.

The single KV store does not differentiate data by device. If the same key is modified by different devices, the data will be overwritten.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [SINGLE_VERSION](arkts-arkdata-distributedkvstore-kvstoretype-e.md#single_version)

<!--Device-KVStoreType-SINGLE_VERSION = 1--><!--Device-KVStoreType-SINGLE_VERSION = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
