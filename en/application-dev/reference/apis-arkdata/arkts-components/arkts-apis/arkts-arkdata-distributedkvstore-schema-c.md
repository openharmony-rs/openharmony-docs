# Schema

```TypeScript
class Schema
```

Defines the schema of a KV store. You can create a **Schema** object and pass it in [Options](arkts-arkdata-distributedkvstore-options-i.md) when creating or opening a KV store.

**Since:** 9

<!--Device-distributedKVStore-class Schema--><!--Device-distributedKVStore-class Schema-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## constructor

```TypeScript
constructor()
```

Defines a constructor used to create a **Schema** instance.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-constructor()--><!--Device-Schema-constructor()-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Examples**

```TypeScript
let child1 = new distributedKVStore.FieldNode('id');
child1.type = distributedKVStore.ValueType.INTEGER;
child1.nullable = false;
child1.default = '1';
let child2 = new distributedKVStore.FieldNode('name');
child2.type = distributedKVStore.ValueType.STRING;
child2.nullable = false;
child2.default = 'zhangsan';

let schema = new distributedKVStore.Schema();
schema.root.appendChild(child1);
schema.root.appendChild(child2);
schema.indexes = ['$.id', '$.name'];
schema.mode = 1;
schema.skip = 0;
```

## indexes

```TypeScript
get indexes(): Array<string>
```

Get the string array of json.

**Type:** Array&lt;string&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-get indexes(): Array<string>--><!--Device-Schema-get indexes(): Array<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

```TypeScript
set indexes(indexes: Array<string>)
```

Set the string array of json.

**Type:** Array&lt;string&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-set indexes(indexes: Array<string>)--><!--Device-Schema-set indexes(indexes: Array<string>)-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## mode

```TypeScript
get mode(): number
```

Get the mode of schema.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-get mode(): int--><!--Device-Schema-get mode(): int-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

```TypeScript
set mode(mode: number)
```

Set the mode of schema.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-set mode(mode: int)--><!--Device-Schema-set mode(mode: int)-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## root

```TypeScript
get root(): FieldNode
```

Get the root json object.

**Type:** [FieldNode](arkts-arkdata-distributedkvstore-fieldnode-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-get root(): FieldNode--><!--Device-Schema-get root(): FieldNode-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

```TypeScript
set root(root: FieldNode)
```

Set the root json object.

**Type:** [FieldNode](arkts-arkdata-distributedkvstore-fieldnode-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-set root(root: FieldNode)--><!--Device-Schema-set root(root: FieldNode)-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## skip

```TypeScript
get skip(): number
```

Get the skip size of schema.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-get skip(): int--><!--Device-Schema-get skip(): int-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

```TypeScript
set skip(skip: number)
```

Set the skip size of schema.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-Schema-set skip(skip: int)--><!--Device-Schema-set skip(skip: int)-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
