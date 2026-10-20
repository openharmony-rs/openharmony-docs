# Entry

```TypeScript
interface Entry
```

Defines the KV pairs stored in a KV store.

**Since:** 9

<!--Device-distributedKVStore-interface Entry--><!--Device-distributedKVStore-interface Entry-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## key

```TypeScript
key: string
```

Key name. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md).

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Entry-key: string--><!--Device-Entry-key: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## value

```TypeScript
value: Value
```

Value object of the KV pair.

**Type:** [Value](arkts-arkdata-distributedkvstore-value-i.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Entry-value: Value--><!--Device-Entry-value: Value-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
