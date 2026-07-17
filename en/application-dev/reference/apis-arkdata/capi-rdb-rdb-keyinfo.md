# Rdb_KeyInfo
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:35.321Z pushedAt=2026-06-29T02:15:43.567Z -->

```c
typedef struct {...} Rdb_KeyInfo
```

## Overview

Defines a struct for the primary key or number of the row that changes.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                    | Description                                                        |
| ---------------------------------------- | ------------------------------------------------------------ |
| int count                                | Number of the changed primary keys or row numbers.                          |
| int type                                 | Type of the primary key. For details, see [OH_ColumnType](capi-oh-data-value-h.md#oh_columntype).|
| [Rdb_KeyData](capi-rdb-rdb-keydata.md)* data | Pointer to the changed data.                                          |