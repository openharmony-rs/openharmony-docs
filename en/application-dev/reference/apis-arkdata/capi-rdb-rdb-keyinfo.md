# Rdb_KeyInfo
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=81165a532e10b3d1517ed6f395ac6f3808130ce3 translatedAt=2026-09-15T10:52:54.818Z pushedAt=2026-09-16T07:50:15.684Z -->

```c
typedef struct Rdb_KeyInfo {...} Rdb_KeyInfo
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
| int type                                 | [OH_ColumnType](capi-oh-data-value-h.md#oh_columntype) of the primary key or row number. |
| [Rdb_KeyData](capi-rdb-rdb-keydata.md)* data | Specific data that has changed.                                           |

