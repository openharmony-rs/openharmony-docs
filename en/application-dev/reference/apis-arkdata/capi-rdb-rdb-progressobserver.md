# Rdb_ProgressObserver
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=92fad92320c327a07cb31c689545113f874871a6 translatedAt=2026-06-26T06:35:37.262Z pushedAt=2026-06-29T02:15:43.569Z -->

```c
typedef struct Rdb_ProgressObserver {...} Rdb_ProgressObserver
```

## Overview

Defines a struct for the observer for the device-cloud sync progress.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member Variables

| Name                                                        | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| void* context                                                | Context of the device-cloud sync progress observer.  |
| [Rdb_ProgressCallback](capi-relational-store-h.md#rdb_progresscallback) callback | Callback used to return the device-cloud sync progress.|