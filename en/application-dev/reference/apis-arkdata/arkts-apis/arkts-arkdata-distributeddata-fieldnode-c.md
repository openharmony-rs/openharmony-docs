# FieldNode

```TypeScript
class FieldNode
```

Represents a **Schema** instance, which provides the APIs for defining the values stored in a KV store.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** FieldNode

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## Modules to Import

```TypeScript
```

## appendChild

```TypeScript
appendChild(child: FieldNode): boolean
```

Appends a child node to this **FieldNode**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** appendChild

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| child | [FieldNode](arkts-arkdata-distributeddata-fieldnode-c.md) | Yes | Child node to append. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
import ddm from '@ohos.data.distributedData';
try {
    let node = new ddm.FieldNode("root");
    let child1 = new ddm.FieldNode("child1");
    let child2 = new ddm.FieldNode("child2");
    let child3 = new ddm.FieldNode("child3");
    node.appendChild(child1);
    node.appendChild(child2);
    node.appendChild(child3);
    console.info("appendNode " + JSON.stringify(node));
    child1 = null;
    child2 = null;
    child3 = null;
    node = null;
} catch (e) {
    console.error("AppendChild " + e);
}
```

## constructor

```TypeScript
constructor(name: string)
```

A constructor used to create a **FieldNode** instance with a string field.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Value of **FieldNode**. |

## default

```TypeScript
default: string
```

Default value of a **FieldNode**.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** default

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## nullable

```TypeScript
nullable: boolean
```

Whether the database field can be null.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** nullable

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## type

```TypeScript
type: number
```

Value of the data type corresponding to the specified node.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** type

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
