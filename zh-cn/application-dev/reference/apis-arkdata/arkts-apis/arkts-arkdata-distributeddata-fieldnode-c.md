# FieldNode

表示 Schema 实例的节点，提供定义存储在数据库中的值的方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** FieldNode

<!--Device-distributedData-class FieldNode--><!--Device-distributedData-class FieldNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## appendChild

```TypeScript
appendChild(child: FieldNode): boolean
```

在当前 FieldNode 中添加一个子节点。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** appendChild

<!--Device-FieldNode-appendChild(child: FieldNode): boolean--><!--Device-FieldNode-appendChild(child: FieldNode): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FieldNode](arkts-arkdata-distributeddata-fieldnode-c.md) | 是 | 要附加的域节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示子节点成功添加到FieldNode；返回false则表示操作失败。 |

**示例：**

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
    console.log("appendNode " + JSON.stringify(node));
    child1 = null;
    child2 = null;
    child3 = null;
    node = null;
} catch (e) {
    console.log("AppendChild " + e);
}

```

## constructor

```TypeScript
constructor(name: string)
```

用于创建带有string字段FieldNode实例的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-FieldNode-constructor(name: string)--><!--Device-FieldNode-constructor(name: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | FieldNode的值。 |

## default

```TypeScript
default: string
```

表示Fieldnode的默认值。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** default

<!--Device-FieldNode-default: string--><!--Device-FieldNode-default: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## nullable

```TypeScript
nullable: boolean
```

表示数据库字段是否可以为空。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** nullable

<!--Device-FieldNode-nullable: boolean--><!--Device-FieldNode-nullable: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## type

```TypeScript
type: number
```

表示指定节点对应数据类型的值。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** type

<!--Device-FieldNode-type: number--><!--Device-FieldNode-type: number-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

