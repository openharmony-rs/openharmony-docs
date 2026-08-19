# @ohos.data.rdb

关系型数据库（Relational Database，RDB）是一种基于关系模型来管理数据的数据库。关系型数据库基于SQLite组件提供了一套完整的对本地数据库进行管理的机制，对外提供了一系列的增、删、改、查等接口，也可以直接运行用户 输入的SQL语句来满足复杂的场景需要。不支持Worker线程。 该模块提供以下关系型数据库相关的常用功能： - [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md)：数据库中用来代表数据实体的性质、特征或者数据实体之间关系的词项，主要用来定义数据库的操作条件。 - [RdbStore](arkts-arkdata-rdb-rdbstore-i.md)：提供管理关系数据库（RDB）方法的接口。 > **说明：** > > - 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.data.relationalStore](arkts-data-relationalstore.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [relationalStore](arkts-data-relationalstore.md)

<!--Device-unnamed-declare namespace rdb--><!--Device-unnamed-declare namespace rdb-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deleteRdbStore](arkts-arkdata-rdb-deleterdbstore-f.md) | 删除数据库，使用callback异步回调。 |
| [deleteRdbStore](arkts-arkdata-rdb-deleterdbstore-f.md) | 使用指定的数据库文件配置删除数据库，使用Promise异步回调。 |
| [getRdbStore](arkts-arkdata-rdb-getrdbstore-f.md) | 获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用callback异步回调。 |
| [getRdbStore](arkts-arkdata-rdb-getrdbstore-f.md) | 获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | 表示关系型数据库（RDB）的谓词。该类确定RDB中条件表达式的值是true还是false。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [RdbStore](arkts-arkdata-rdb-rdbstore-i.md) | 提供管理关系数据库（RDB）方法的接口。 在使用以下相关接口前，请使用 [executeSql](arkts-arkdata-rdb-rdbstore-i.md#executesql) 接口初始化数据库表结构和相关数据。 |
| [StoreConfig](arkts-arkdata-rdb-storeconfig-i.md) | 管理关系数据库配置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubscribeType](arkts-arkdata-rdb-subscribetype-e.md) | 描述订阅类型。 |
| [SyncMode](arkts-arkdata-rdb-syncmode-e.md) | 指数据库同步模式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ResultSet](arkts-arkdata-rdb-resultset-t.md) | 配置RdbPredicates以匹配数据字段为ValueType且value超出给定范围的指定字段。该方法等同于SQL语句中的"NOT BETWEEN"。 |
| [ValueType](arkts-arkdata-rdb-valuetype-t.md) | 用于表示允许的数据字段类型。 |
| [ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md) | 用于存储键值对的类型。 |

