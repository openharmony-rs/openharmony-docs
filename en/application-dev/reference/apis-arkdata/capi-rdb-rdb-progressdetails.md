# Rdb_ProgressDetails
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=7799dc9b15464fe12af62fdda50a1eed7604a593 translatedAt=2026-09-04T03:05:22.090Z pushedAt=2026-09-09T09:11:03.680Z -->

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
| int version         | Version of the **Rdb_ProgressDetails** struct. |
| int schedule        | Device-cloud sync process.                     |
| int code            | Status code of the device-cloud sync process.                |
| int32_t tableLength | Number of the tables synced between the device and cloud.               |

