# Rdb_SubscribeCallback

```c
typedef union Rdb_SubscribeCallback {...} Rdb_SubscribeCallback
```

## 概述

表示回调函数。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**起始版本：** 11

**相关模块：** [RDB](capi-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Rdb_DetailsObserver](capi-relational-store-h.md#rdb_detailsobserver) detailsObserver | 云端数据变更详情事件的回调函数。 |
| [Rdb_BriefObserver](capi-relational-store-h.md#rdb_briefobserver) briefObserver | 云端数据变更事件的回调函数。 |


