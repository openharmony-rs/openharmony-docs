# OH_Rdb_Config
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=25e362cbd0c84d5eeff6cfae5eb123fa6f04919a translatedAt=2026-09-15T10:44:40.318Z pushedAt=2026-09-16T07:50:15.666Z -->

```c
typedef struct  {...} OH_Rdb_Config
```

## Overview

Defines the RDB store configuration.

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                   | Description                                                        |
| ----------------------- | ------------------------------------------------------------ |
| int selfSize            | Size of the struct.                                            |
| const char* dataBaseDir | Directory of the database file. The full path consists of **dataBaseDir** and **storeName**, and its total length cannot exceed 1024 characters. It cannot be empty.                                             |
| const char* storeName   | Database name. It cannot be empty and cannot contain the path separator /.                                                 |
| const char* bundleName  | Application bundle name. It cannot be empty.                                                   |
| const char* moduleName  | Application module name. It cannot be empty.                                                 |
| bool isEncrypt          | Whether to encrypt the RDB store. The value **true** means to encrypt the RDB store; the value **false** means the opposite.            |
| int securityLevel       | Database security level [OH_Rdb_SecurityLevel](capi-relational-store-h.md#oh_rdb_securitylevel). |
| int area                | Database security area level [Rdb_SecurityArea](capi-relational-store-h.md#rdb_securityarea)<br>**Since:** 11 |

