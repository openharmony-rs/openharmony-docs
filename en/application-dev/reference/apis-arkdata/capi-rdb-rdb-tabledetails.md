# Rdb_TableDetails
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1054d8b030836fe58bcf3a3108bf6f34b102d289 translatedAt=2026-09-15T10:54:50.641Z pushedAt=2026-09-16T07:50:15.692Z -->

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

