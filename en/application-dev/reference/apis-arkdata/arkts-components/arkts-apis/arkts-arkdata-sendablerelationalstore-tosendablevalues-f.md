# toSendableValues

## Modules to Import

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';
```

## toSendableValues

```TypeScript
function toSendableValues(values: NonSendableValues): collections.Array<ValueType>
```

Converts the array data that cannot be passed across threads into the data that can be passed across threads.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [NonSendableValues](arkts-arkdata-sendablerelationalstore-nonsendablevalues-t.md) | Yes | Array data that cannot be passed across threads. |

**Return value:**

| Type | Description |
| --- | --- |
| [collections.Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)&lt;[ValueType](arkts-arkdata-sendablerelationalstore-valuetype-t.md)&gt; | Array data that can be passed across threads. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { relationalStore, sendableRelationalStore } from '@kit.ArkData';
const array: relationalStore.ValueType[] = [];
array.push(1);
array.push(2);
array.push("aaaaaa")
const values = sendableRelationalStore.toSendableValues(array);
```
