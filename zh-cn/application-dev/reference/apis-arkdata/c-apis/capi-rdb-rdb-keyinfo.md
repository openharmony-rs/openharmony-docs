# Rdb_KeyInfo

```c
typedef struct Rdb_KeyInfo {...} Rdb_KeyInfo
```

## 概述

描述发生变化的行的主键或者行号。

**起始版本：** 11

**相关模块：** [RDB](capi-rdb.md)

**所在头文件：** [relational_store.h](capi-relational-store-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int count | 表示发生变化的主键或者行号的数量。 |
| int type | 表示主键或行号的数据类型[OH_ColumnType](capi-oh-data-value-h.md#oh_columntype)。 |
| union Rdb_KeyData |  |
| uint64_t integer | 表示uint64_t类型的数据。 |
| double real | 表示double类型的数据。 |
| const char *text; } *data | 表示const char *类型的数据。 |


