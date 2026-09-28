# Rdb_ProgressDetails
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bb88bb94d89f6d282aea4674234254f4d4bb26 translatedAt=2026-09-15T10:53:27.261Z pushedAt=2026-09-16T07:50:15.686Z -->

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

