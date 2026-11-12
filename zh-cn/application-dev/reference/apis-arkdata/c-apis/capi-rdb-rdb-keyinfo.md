# Rdb_KeyInfo

```c
typedef struct Rdb_KeyInfo {...} Rdb_KeyInfo
```

## 概述

描述发生变化的行的主键或者行号。

<!--Device-struct Rdb_KeyInfo {...}--><!--Device-struct Rdb_KeyInfo {...}-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**起始版本：** 11

**相关模块：** [RDB](capi-arkdata-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int count | 表示发生变化的主键或者行号的数量。 |
| int type | 表示主键或行号的数据类型[OH_ColumnType](capi-oh-data-value-h.md#oh_columntype)。 |
| data | 表示密钥信息的数据。<br>**起始版本：** 11 |
| data.integer | 表示uint64_t类型的数据。 |
| data.real | 表示double类型的数据。 |
| data.text | 表示const char *类型的数据。 |


