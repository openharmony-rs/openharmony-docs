# Schema

表示数据库模式，可以在创建或打开数据库时创建Schema对象并将它们放入[Options](arkts-arkdata-distributedkvstore-options-i.md)中。

STRICT：STRICT模式要求用户插入的值必须与Schema定义严格匹配，字段数量和格式都不能有差异。如果不匹配，数据库将在插入数据时返回错误。

COMPATIBLE：选择为COMPATIBLE模式时，数据库在检查Value格式时较为宽松，只要Value具有Schema描述的特征即可，允许存在额外字段。例如，定义了id、name字段时，可以插入id、name、age等多个字段。

**起始版本：** 9

<!--Device-distributedKVStore-class Schema--><!--Device-distributedKVStore-class Schema-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## constructor

```TypeScript
constructor()
```

用于创建Schema实例的构造函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Schema-constructor()--><!--Device-Schema-constructor()-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**示例：**

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
set indexes(indexes: Array<string>)
```

设置索引字段定义

**类型：** Array<string>

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Schema-set indexes(indexes: Array<string>)--><!--Device-Schema-set indexes(indexes: Array<string>)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## mode

```TypeScript
set mode(mode: number)
```

设置Schema的模式。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Schema-set mode(mode: int)--><!--Device-Schema-set mode(mode: int)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## root

```TypeScript
set root(root: FieldNode)
```

设置Value中所有字段的定义。

**类型：** FieldNode

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Schema-set root(root: FieldNode)--><!--Device-Schema-set root(root: FieldNode)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## skip

```TypeScript
set skip(skip: number)
```

设置跳过的字节数。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Schema-set skip(skip: int)--><!--Device-Schema-set skip(skip: int)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

