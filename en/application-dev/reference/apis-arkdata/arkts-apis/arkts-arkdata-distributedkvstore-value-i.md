# Value

```TypeScript
interface Value
```

Defines the **value** object in a KV store.

**Since:** 9

<!--Device-distributedKVStore-interface Value--><!--Device-distributedKVStore-interface Value-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## type

```TypeScript
type: ValueType
```

Type of the value.

**Type:** [ValueType](arkts-arkdata-distributedkvstore-valuetype-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Value-type: ValueType--><!--Device-Value-type: ValueType-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## value

```TypeScript
value: Uint8Array | string | number | boolean
```

Value in a key-value pair. The length of the Uint8Array and string types ranges from 0 to [MAX_VALUE_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). The value range of the number and boolean types is determined by their own types.

**Type:** Uint8Array &#124; string &#124; number &#124; boolean

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Value-value: Uint8Array | string | long | double | boolean--><!--Device-Value-value: Uint8Array | string | long | double | boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
