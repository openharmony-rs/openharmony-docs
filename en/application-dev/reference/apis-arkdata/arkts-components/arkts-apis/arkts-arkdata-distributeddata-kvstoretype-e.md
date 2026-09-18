# KVStoreType

Enumerates the KV store types.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** KVStoreType

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## DEVICE_COLLABORATION

```TypeScript
DEVICE_COLLABORATION = 0
```

Device KV store.

The device KV store manages data by device, which eliminates conflicts. Data can be queried by device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** DEVICE_COLLABORATION

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## SINGLE_VERSION

```TypeScript
SINGLE_VERSION = 1
```

Single KV store.

The single KV store does not differentiate data by device. If the same key is modified by different devices, the data will be overwritten.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** SINGLE_VERSION

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MULTI_VERSION

```TypeScript
MULTI_VERSION = 2
```

Multi-version KV store. This type is not supported currently.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
