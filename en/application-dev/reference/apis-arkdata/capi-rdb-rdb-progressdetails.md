# Rdb_ProgressDetails
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:38.940Z pushedAt=2026-06-29T02:15:43.571Z -->

```c
typedef struct Rdb_ProgressDetails {...} Rdb_ProgressDetails
```

## Overview

Defines a struct for statistics of the overall device-cloud sync (upload and download) tasks of an RDB store.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name               | Description                                   |
| ------------------- | --------------------------------------- |
| int version         | Version of the **OH_TableDetails** struct.|
| int schedule        | Device-cloud sync process.                     |
| int code            | Device-cloud sync state.               |
| int32_t tableLength | Number of the tables synced between the device and cloud.               |