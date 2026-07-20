# Schema

表示数据库模式，可以在创建或打开数据库时创建Schema对象并将它们放入[Options](arkts-arkdata-distributeddata-options-i.md)中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** Schema

<!--Device-distributedData-class Schema--><!--Device-distributedData-class Schema-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

用于创建Schema实例的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-Schema-constructor()--><!--Device-Schema-constructor()-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## indexes

```TypeScript
indexes: Array<string>
```

表示json类型的字符串数组。

**类型：** Array&lt;string&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** indexes

<!--Device-Schema-indexes: Array<string>--><!--Device-Schema-indexes: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## mode

```TypeScript
mode: number
```

表示Schema的模式。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** mode

<!--Device-Schema-mode: number--><!--Device-Schema-mode: number-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## root

```TypeScript
root: FieldNode
```

表示json根对象。

**类型：** FieldNode

**起始版本：** 8

**废弃版本：** 9

**替代接口：** root

<!--Device-Schema-root: FieldNode--><!--Device-Schema-root: FieldNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## skip

```TypeScript
skip: number
```

Schema的跳跃大小。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** skip

<!--Device-Schema-skip: number--><!--Device-Schema-skip: number-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

