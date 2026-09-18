# OH_Rdb_Config

```c
typedef struct OH_Rdb_Config {...} OH_Rdb_Config
```

## Overview

Manages relational database configurations.

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int selfSize | Indicates the size of the [OH_Rdb_Config](capi-rdb-oh-rdb-config.md). It is mandatory. |
| const char *dataBaseDir | Indicates the directory of the database. |
| const char *storeName | Indicates the name of the database. |
| const char *bundleName | Indicates the bundle name of the application. |
| const char *moduleName | Indicates the module name of the application. |
| bool isEncrypt | Indicates whether the database is encrypted. |
| int securityLevel | Indicates the security level [OH_Rdb_SecurityLevel](capi-relational-store-h.md#oh_rdb_securitylevel) of the database. |
| int area |  |


