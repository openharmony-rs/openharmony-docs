# Rdb_ChangeInfo
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=17e4b320c8985512791b8b37fea849963e9ff387 translatedAt=2026-09-04T03:03:53.994Z pushedAt=2026-09-09T09:11:03.677Z -->

```c
typedef struct Rdb_ChangeInfo {...} Rdb_ChangeInfo
```

## Overview

Defines a struct for the details about the device-cloud sync process.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                       | Description                                                        |
| ------------------------------------------- | ------------------------------------------------------------ |
| int version                                 | Used to uniquely identify the version of the **Rdb_ChangeInfo** struct.                |
| const char* tableName                       | Name of the table with data changes.                                    |
| int ChangeType                              | Type of the changed data. The value **0** indicates data changes, and **1** indicates asset attachment changes.         |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) inserted | Location where data is inserted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the inserted data.|
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) updated  | Location where data is updated. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the updated data.|
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) deleted  | Location where data is deleted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the deleted data.|

