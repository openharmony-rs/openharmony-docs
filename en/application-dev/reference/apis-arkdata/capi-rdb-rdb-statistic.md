# Rdb_Statistic
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1054d8b030836fe58bcf3a3108bf6f34b102d289 translatedAt=2026-09-15T10:54:21.615Z pushedAt=2026-09-16T07:50:15.689Z -->

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

