# OH_Rdb_Store
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=25e362cbd0c84d5eeff6cfae5eb123fa6f04919a translatedAt=2026-09-15T10:46:09.067Z pushedAt=2026-09-16T07:50:15.672Z -->

```c
typedef struct {...} OH_Rdb_Store
```

## Overview

Represents a database instance, which is obtained through functions such as [OH_Rdb_GetOrOpen](capi-relational-store-h.md#oh_rdb_getoropen) or [OH_Rdb_CreateOrOpen](capi-relational-store-h.md#oh_rdb_createoropen).

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name      | Description                            |
| ---------- | -------------------------------- |
| int64_t id | Unique identifier of the **OH_Rdb_Store** struct.|

