# OH_Rdb_Config

```c
typedef struct OH_Rdb_Config {...} OH_Rdb_Config
```

## Overview

Manages relational database configurations.

<!--Device-typedef struct OH_Rdb_Config {...} OH_Rdb_Config--><!--Device-typedef struct OH_Rdb_Config {...} OH_Rdb_Config-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int selfSize | Indicates the size of the [OH_Rdb_Config](capi-rdb-oh-rdb-config.md). It is mandatory.<br><!--Device-int selfSize--><!--Device-int selfSize-End--> |
| const char *dataBaseDir | Indicates the directory of the database.<br><!--Device-const char *dataBaseDir--><!--Device-const char *dataBaseDir-End--> |
| const char *storeName | Indicates the name of the database.<br><!--Device-const char *storeName--><!--Device-const char *storeName-End--> |
| const char *bundleName | Indicates the bundle name of the application.<br><!--Device-const char *bundleName--><!--Device-const char *bundleName-End--> |
| const char *moduleName | Indicates the module name of the application.<br><!--Device-const char *moduleName--><!--Device-const char *moduleName-End--> |
| bool isEncrypt | Indicates whether the database is encrypted.<br><!--Device-bool isEncrypt--><!--Device-bool isEncrypt-End--> |
| int securityLevel | Indicates the security level [OH_Rdb_SecurityLevel](capi-relational-store-h.md#oh_rdb_securitylevel) of the database.<br><!--Device-int securityLevel--><!--Device-int securityLevel-End--> |
| int area | Indicates the security area [Rdb_SecurityArea](capi-relational-store-h.md#rdb_securityarea) of the database.<br>**Since**: 11<br><!--Device-int area--><!--Device-int area-End--> |


