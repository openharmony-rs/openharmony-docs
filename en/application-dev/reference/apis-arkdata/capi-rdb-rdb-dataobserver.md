# Rdb_DataObserver
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:18.579Z pushedAt=2026-06-29T02:15:43.562Z -->

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