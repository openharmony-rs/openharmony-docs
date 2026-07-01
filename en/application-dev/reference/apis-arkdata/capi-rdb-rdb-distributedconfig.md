# Rdb_DistributedConfig
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:20.531Z pushedAt=2026-06-29T02:15:43.565Z -->

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
| int version     | Version of the **Rdb_DistributedConfig** struct.|
| bool isAutoSync | Whether the table supports automatic device-cloud synchronization. If the value is **true**, the system automatically triggers device-cloud synchronization. If the value is **false**, the system does not automatically trigger device-cloud synchronization. In this case, you need to call [OH_Rdb_CloudSync](capi-relational-store-h.md#oh_rdb_cloudsync) to trigger device-cloud synchronization.|