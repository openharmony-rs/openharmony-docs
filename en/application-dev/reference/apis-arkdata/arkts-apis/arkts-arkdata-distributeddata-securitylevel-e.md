# SecurityLevel

Enumerates the KV store security levels.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** SecurityLevel

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## NO_LEVEL

```TypeScript
NO_LEVEL = 0
```

No security level is set for the KV store (deprecated).

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## S0

```TypeScript
S0 = 1
```

The KV store security level is public (deprecated).

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S1

```TypeScript
S1 = 2
```

Low security level. If data leakage occurs, minor impact will be caused. For example, a KV store that contains system data such as wallpapers.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** S1

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S2

```TypeScript
S2 = 3
```

Medium security level. If data leakage occurs, moderate impact will be caused. For example, a KV store that contains information created by users or call records, such as audio or video clips.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** S2

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S3

```TypeScript
S3 = 5
```

High security level. If data leakage occurs, major impact will be caused. For example, a KV store that contains information such as user fitness, health, and location data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** S3

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S4

```TypeScript
S4 = 6
```

Critical security level. If data leakage occurs, severe impact will be caused. For example, a KV store that contains information such as authentication credentials and financial data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** S4

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
