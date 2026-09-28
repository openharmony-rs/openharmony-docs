# Rdb_DataObserver
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1054d8b030836fe58bcf3a3108bf6f34b102d289 translatedAt=2026-09-15T10:51:14.950Z pushedAt=2026-09-16T07:50:15.680Z -->

```c
typedef struct Rdb_DataObserver {...} Rdb_DataObserver
```

## Overview

Defines a struct for the data observer.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                                        | Description                    |
| ------------------------------------------------------------ | ------------------------ |
| void* context                                                | Pointer to the context of the data observer.|
| [Rdb_SubscribeCallback](capi-rdb-rdb-subscribecallback.md) callback | Callback used to return the result.      |

