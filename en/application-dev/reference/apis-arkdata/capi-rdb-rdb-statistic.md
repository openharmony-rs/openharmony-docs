# Rdb_Statistic
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:37.778Z pushedAt=2026-06-29T02:15:43.568Z -->

```c
typedef struct Rdb_Statistic {...} Rdb_Statistic
```

## Overview

Defines a struct for the device-cloud sync statistics of a database table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name          | Description                                    |
| -------------- | ---------------------------------------- |
| int total      | Total number of rows to be synced between the device and cloud in the database table.    |
| int successful | Number of rows that are successfully synced between the device and cloud in the database table.      |
| int failed     | Number of rows that failed to be synced between the device and cloud in the database table.      |
| int remained   | Number of rows that are not executed for device-cloud sync in the database table.|