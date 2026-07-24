# Rdb_TableDetails
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:53.593Z pushedAt=2026-06-29T02:15:43.573Z -->

```c
typedef struct Rdb_TableDetails {...} Rdb_TableDetails
```

## Overview

Defines a struct for statistics of device-cloud upload and download tasks of a database table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                           | Description                                      |
| ----------------------------------------------- | ------------------------------------------ |
| const char* table                               | Database table name.                              |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) upload   | Statistics of the device-cloud upload tasks.|
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) download | Statistics of the device-cloud download tasks.|