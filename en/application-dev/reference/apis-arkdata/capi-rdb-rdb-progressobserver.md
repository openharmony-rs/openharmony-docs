# Rdb_ProgressObserver
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1054d8b030836fe58bcf3a3108bf6f34b102d289 translatedAt=2026-09-15T10:54:04.228Z pushedAt=2026-09-16T07:50:15.688Z -->

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

