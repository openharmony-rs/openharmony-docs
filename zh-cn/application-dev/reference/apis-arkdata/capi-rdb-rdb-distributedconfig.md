# Rdb_DistributedConfig
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

```c
typedef struct Rdb_DistributedConfig {...} Rdb_DistributedConfig
```

## 概述

记录表的分布式配置信息。

**起始版本：** 11

**相关模块：** [RDB](capi-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称            | 描述                                          |
| --------------- | --------------------------------------------- |
| int version     | 用于唯一标识Rdb_DistributedConfig结构的版本。 |
| bool isAutoSync | 表示该表是否支持端云自动同步。为true时，支持系统自动触发端云同步；为false时不支持系统自动触发端云同步，需要调用[OH_Rdb_CloudSync](capi-relational-store-h.md#oh_rdb_cloudsync)接口触发端云同步。 |

