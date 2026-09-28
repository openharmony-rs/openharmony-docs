# Rdb_ChangeInfo
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=25e362cbd0c84d5eeff6cfae5eb123fa6f04919a translatedAt=2026-09-15T10:50:35.849Z pushedAt=2026-09-16T07:50:15.679Z -->

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
| int version                                 |  Used to uniquely identify the version of the **Rdb_ChangeInfo** struct.                |
| const char* tableName                       | Name of the table with data changes.                                    |
| int ChangeType                              | Type of the changed data. The value **0** indicates data changes, and **1** indicates asset attachment changes.         |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) inserted | Location where data is inserted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the inserted data.|
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) updated  | Location where data is updated. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the updated data.|
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) deleted  | Location where data is deleted. If the primary key of the table is of the string type, it is the value of the primary key. Otherwise, it is the row number of the deleted data.|

