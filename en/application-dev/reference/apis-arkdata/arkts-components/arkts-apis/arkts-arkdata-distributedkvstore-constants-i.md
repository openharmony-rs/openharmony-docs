# Constants

Provides constants of the distributed KV store.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## MAX_BATCH_SIZE

```TypeScript
readonly MAX_BATCH_SIZE: number
```

Maximum number of batch operations allowed, which is 128.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MAX_KEY_LENGTH

```TypeScript
readonly MAX_KEY_LENGTH: number
```

Maximum length of a key in the database, which is 1024 bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MAX_KEY_LENGTH_DEVICE

```TypeScript
readonly MAX_KEY_LENGTH_DEVICE: number
```

Maximum length of a key in a device KV store, which is 896 bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MAX_QUERY_LENGTH

```TypeScript
readonly MAX_QUERY_LENGTH: number
```

Maximum query length, which is 512000 bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MAX_STORE_ID_LENGTH

```TypeScript
readonly MAX_STORE_ID_LENGTH: number
```

Maximum length of a KV store ID, which is 128 bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## MAX_VALUE_LENGTH

```TypeScript
readonly MAX_VALUE_LENGTH: number
```

Maximum length of a value in the database, which is 4194303 bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
