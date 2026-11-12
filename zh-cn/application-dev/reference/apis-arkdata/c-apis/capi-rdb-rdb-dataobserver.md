# Rdb_DataObserver

```c
typedef struct Rdb_DataObserver {...} Rdb_DataObserver
```

## 概述

表示数据观察者。

<!--Device-struct Rdb_DataObserver {...}--><!--Device-struct Rdb_DataObserver {...}-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**起始版本：** 11

**相关模块：** [RDB](capi-arkdata-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void *context | 表示数据观察者的上下文。 |
| [Rdb_SubscribeCallback](capi-rdb-rdb-subscribecallback.md) callback | 数据观察者的回调。 |


