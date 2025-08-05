# Rdb_Statistic
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--SE: @widecode; @htt1997-->
<!--TSE: @yippo; @logic42-->

## 概述

描述数据库表的端云同步过程的统计信息。

**起始版本：** 11

**相关模块：** [RDB](capi-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称           | 描述                                     |
| -------------- | ---------------------------------------- |
| int total      | 表示数据库表中需要端云同步的总行数。     |
| int successful | 表示数据库表中端云同步成功的行数。       |
| int failed     | 表示数据库表中端云同步失败的行数。       |
| int remained   | 表示数据库表中端云同步剩余未执行的行数。 |

