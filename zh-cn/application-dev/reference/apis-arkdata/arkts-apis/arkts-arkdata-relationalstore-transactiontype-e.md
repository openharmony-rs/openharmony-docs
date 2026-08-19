# TransactionType

描述创建事务对象的枚举。请使用枚举名称而非枚举值。

**起始版本：** 23

<!--Device-relationalStore-enum TransactionType--><!--Device-relationalStore-enum TransactionType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## DEFERRED

```TypeScript
DEFERRED = 0
```

表示创建一个DEFERRED类型的事务对象，该类型的事务对象在创建时只会关闭自动提交而不会真正开始事务，只有在首次读或写操作时会真正开始一个读或写事务。

**起始版本：** 23

<!--Device-TransactionType-DEFERRED = 0--><!--Device-TransactionType-DEFERRED = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## IMMEDIATE

```TypeScript
IMMEDIATE = 1
```

表示创建一个IMMEDIATE类型的事务对象，该类型的事务对象在创建时会真正开始一个写事务；如果有别的写事务未提交，则会创建失败，返回错误码14800024。

**起始版本：** 23

<!--Device-TransactionType-IMMEDIATE = 1--><!--Device-TransactionType-IMMEDIATE = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## EXCLUSIVE

```TypeScript
EXCLUSIVE = 2
```

表示创建一个EXCLUSIVE类型的事务对象，该类型的事务在WAL模式下和IMMEDIATE相同，但在其他日志模式下能够防止事务期间有其他连接读取数据库。

**起始版本：** 23

<!--Device-TransactionType-EXCLUSIVE = 2--><!--Device-TransactionType-EXCLUSIVE = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

