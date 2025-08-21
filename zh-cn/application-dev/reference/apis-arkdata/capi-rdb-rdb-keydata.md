# Rdb_KeyData
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 概述

存放变化的具体数据。

**相关模块：** [RDB](capi-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称             | 描述                     |
| ---------------- | ------------------------ |
| uint64_t integer | 存放uint64_t类型的数据。 |
| double real      | 存放double类型的数据。   |
| const char* text | 存放char类型的数据。     |

