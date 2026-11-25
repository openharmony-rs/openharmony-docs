# Rdb_KeyInfo
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=a344fa18476f0d16c0d531be44b7138a04f15161 translatedAt=2026-11-16T01:36:15.039Z pushedAt=2026-11-20T07:27:07.827Z nl=1 -->

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

