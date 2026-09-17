# Rdb_DistributedConfig
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4029353a2603444f2bedb0389028b8df4055b070 translatedAt=2026-09-15T10:51:37.188Z pushedAt=2026-09-16T07:50:15.682Z -->

```c
typedef struct Rdb_DistributedConfig {...} Rdb_DistributedConfig
```

## Overview

Defines a struct for distributed configuration of a table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name           | Description                                         |
| --------------- | --------------------------------------------- |
| int version | Version of the **Rdb_DistributedConfig** struct. |
| bool isAutoSync | Whether the table supports automatic device-cloud synchronization. If the value is **true**, the system automatically triggers device-cloud synchronization. If the value is **false**, the system does not automatically trigger device-cloud synchronization. In this case, you need to call [OH_Rdb_CloudSync](capi-relational-store-h.md#oh_rdb_cloudsync) to trigger device-cloud synchronization.|

