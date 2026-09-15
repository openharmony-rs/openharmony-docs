# OH_Rdb_Store
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=7ef9b5061ca4cac695cf7b193861ba482e2c784a translatedAt=2026-09-04T03:01:56.281Z pushedAt=2026-09-09T09:11:03.670Z -->

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

